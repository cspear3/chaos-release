#Virtualization notes

# Virtualization notes #

**- verify you have hardware virtualization support**
> egrep "svm|vmx" /proc/cpuinfo

**Creating a filesystem**
> qemu-img create my\_image.img 100G

**Create a COW filesystem**
> qemu-img create my\_image.img -f qcow2 100G

**Create image to be used by multiple nodes using COW**
> qemu-img create -b my\_image.img -f qcow2 node1.img

> qemu-img create -b my\_image.img -f qcow2 node2.img

**console install using libvirt**
```
 virt-install -n my_domain -r 2048 --vcpus=2 \
             --disk path=/tmp/my_image.img,device=disk \
             --cdrom=/tmp/install_dvd.iso \
             --vnc --os-type linux --accelerate  --hvm
```
**connecting to the console**
> virt-viewer my\_domain

**KVM, sending console to virtual serial port**
> virsh console my\_domain # requires the following in domain image
```

/etc/securetty
ttyS1
ttyS0

/etc/inittab
s0:2345:respawn:/sbin/agetty -L 115200 ttyS0

/boot/grub/grub.conf
title linux
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.9-55.ELsmp ro root=/dev/hda1 console=tty0 console=ttyS0,115200
        initrd /boot/initrd-2.6.9-55.ELsmp.img
```

**Virsh commands**
> virsh dumpxml DOMAIN # dump xml info on domain

> virsh define my\_domain.xml # define a domain based on xml file

> virsh create my\_domain.xml # start a domain based on xml file

> virsh start my\_domain # start my domain, this domain will need defined.

> virsh shutdown my\_domain # run init 0 on my domain

> virsh destroy my\_domain # powers off my doamin

> virsh undefine my\_domain # undefine the domain

> virsh edit my\_domain # edit attributes of a domain.

> virt-viewer my\_domain #

**mounting a qemu or xen image on a loopback**
> Don't do this while the file is in use, else you will corrupt the image
```
 sfdisk -d my_image.img

 my_image.img1 : start=       63, size= 31439142, Id=83, bootable
 my_image.img2 : start= 31439205, size=  2104515, Id=82
 my_image.img3 : start=        0, size=        0, Id= 0
 my_image.img4 : start=        0, size=        0, Id= 0
```
> only one partition, which is "/". you need to offset the mount. So you multiply 63\*512=32256 and
```
 mount -o loop,offset=32256 my_image.img /mnt
```
> If you have more partitions, just multiply the start location by 512 and that is your offset.

**making a XEN image into a KVM image**
> Sorry, but this is a hack. I start by making a install image with qemu-img. I then do a virt-install to that image. I let the install go until it has partitioned and formatted the image. While this is going on. I dump the xml info on the domain. Once the format is done, I then virsh destory my\_domain.

> I then loopback mount the image I just created and the XEN image. I then
```
 rsync -av --delete /xen_mount_point/ /kvm_mount_point/
```
> note you may have more then one partition so you need to deal with that.

> Now you need to go into the KVM image and make some edits, namely grub.conf, and fstab to make sure they match up with your current partition layout. Note in grub.conf your kernel may have been something like /vmlinuz, but because you only have one partition it would need to be /boot/vmlinuz. Same for the initrd.

> now unmount all these loopbacks.

> You now need to fix grub to work on the new image. I edit the xml file that I dumped, and change my boot device and iso location.
```
 <boot dev='cdrom'/>
```
```
    <disk type='file' device='cdrom'>
      <source file='/tmp/install_dvd.iso'/>
      <target dev='hdc' bus='ide'/>
      <readonly/>
    </disk>
```

> then virsh create my\_xml\_dump.xml and go into rescue mode. Once in rescue mode, I chroot into my image and run:
```
 grub-install /dev/hda --recheck
```

> logout and shutdown the image. I then edit the xml image again, change dev='cdrom' to dev='hd' and remove the source file of the cdrom area. I then boot my new KVM image.

> What a hack! Haven't looked, I am sure I can pass to virsh boot info and source files for cdrom. Not sure how to get around the grub install piece.

**NAT interface in KVM**
> Make sure virbr0 is up, and if so, you just need something like this in your xml file:
```
    <interface type='network'>
      <source network='default'/>
      <mac address='00:16:3E:4D:65:05'/>
      <model type='virtio'/>
    </interface>
```

**Bridging a interface for domU using KVM**
> On host node
```
ifconfig virbr0 down

cat /etc/sysconfig/network-scripts/ifcfg-eth1 
DEVICE=eth1
ONBOOT=yes
BRIDGE=br0

cat /etc/sysconfig/network-scripts/ifcfg-br0
DEVICE=br0
ONBOOT=yes
TYPE=Bridge
```
> And in the XML file for the node
```
    <interface type='bridge'>
      <source bridge='br0'/>
      <mac address='00:16:3E:4D:65:05'/>
    </interface>
```


**Bridging a interface for domU using Xen**
> On host node, don't allow Xen to do things, just do it like you do in KVM
```
cat /etc/xen/scripts/network-bridges
/bin/true

cat /etc/sysconfig/network-scripts/ifcfg-eth1 
DEVICE=eth1
ONBOOT=yes
BRIDGE=br0

cat /etc/sysconfig/network-scripts/ifcfg-br0
DEVICE=br0
ONBOOT=yes
TYPE=Bridge
```
> And in the XML file for the node
> And in the cfg file have something like
```
vif = ['bridge=br0,mac=00:16:3E:4D:66:01,type=netfront']
```

**KVM PCI passthrough**
> you need to remove the pci device from the host. Pass the location of the device based on it's `lspci` location. For example 03:00.0 Here is a bad script to do it, I wouldn't use it, but it does give you the idea
```
#!/bin/bash

device=$1

modprobe pci_stub

ID=`lspci -n |grep ^${device} |awk  '{gsub(":"," ")}{print $4,$5}'`
LOCATION="0000:${device}"

echo "${ID}" > /sys/bus/pci/drivers/pci-stub/new_id
echo "${LOCATION}" > /sys/bus/pci/devices/${LOCATION}/driver/unbind
echo "${LOCATION}" > /sys/bus/pci/drivers/pci-stub/bind
```

> There are 2 ways to give this device to your domU, first is at boot time. In the xml file in the devices section add something like:
```
    <hostdev mode='subsystem' type='pci'>
      <source>
        <address bus='0x03' slot='0x00' function='0x0'/>
      </source>
    </hostdev>
```
> where the 3 hex numbers correspond to your device when you run `lcpsi`

> The second way is to just have a separate xml file with the same above info, have your domU booted then run on the host:
```
virsh attach-device YOUR_DOMAIN_NAME YOU_XML_FILE
```

> For whatever reason, the above only works on a Intel node. On an AMD node I get the error
```
error: internal error Not resetting active device 0000:03:00.0
```
> looking into it

**Xen pciback**
> To remove the device from dom0, make sure dom0 is not using it, and find your device using `lspci` and run:
```
modprobe pciback 'hide=(0000:07:00.0)'
```

> Then when you start your xen image run something like:
```
  xm create -c node_1 pci=07:00.0 vm.cfg
```
> And the domU should see the pci device.

**Booting a Xen image diskless**
> your pxelinux.cfg file should have something like this, which also gets you your serial console on ttyS0
```
label linux
   kernel mboot.c32
   append xen-64bit.gz dom0_mem=543M console=com1 com1=115200,8n1 --- vmlinuz-2.6.18-128.2.1.4.9.el5xen console=ttyS0,115200n8 --- initrd-2.6.18-128.2.1.4.9.el5xen
```
> The mboot.c32 comes with the syslinux rpm. copy this file to into the /boot directory of your diskless image. Don't put any ttyS0 info into your inittab, it is not needed to get this console like it is in KVM.
> When using nfsroot, /usr/share/nfsroot/initrd-init needs changed like the following:
```
<    # Commented out for Xen testing
<    #if bootmac=$(nrf_bootmac); then
<    #   if ! nrf_fixeth0 ${bootmac}; then 
<    #      echo "${prog}: error: failed to reassign eth0 to device ${bootmac}" >&2
<    #      panic
<    #   fi
<    #fi
---
>    if bootmac=$(nrf_bootmac); then
>       if ! nrf_fixeth0 ${bootmac}; then 
>          echo "${prog}: error: failed to reassign eth0 to device ${bootmac}" >&2
>          panic
>       fi
>    fi
168,175c167,171
< # Commented out for Xen testing
< #if nrf_bootmac >/dev/null; then
< #   sysroot_nfs
< #else
< #   sysroot_cdrom
< #fi
< 
< sysroot_nfs
```

