# Installing CHAOS 5 rpms on CentOS #

Download and install

http://mirrors.kernel.org/centos/6/isos/x86_64/CentOS-6.4-x86_64-minimal.iso

If not already on the network, edit:

/etc/sysconfig/network-scripts/ifcfg-eth0

and add:

ONBOOT=yes

BOOTPROTO=dhcp

/etc/init.d/network restart

## Install Chaos RPMS ##

```
rpm -Uv ftp://gdo-lc.ucllnl.org/pub/projects/chaos/current/x86_64/chaos-release.rpm

rpm -Uv ftp://gdo-lc.ucllnl.org/pub/projects/chaos/current/x86_64/epel-release.rpm

yum groupinstall Chaos.Base

```

## Useful things you won't get that are in TOSS ##

acml-gnu-4.4
acml-intel-4.4
acml-pathscale-4.0
acml-pgi-4.4
intel-11.1
intel-12.0
intel-12.1
intel-13.0
intel-ocl-1.1
moab
mvapich-1.2-intel
mvapich-1.2-intel-psm
mvapich-1.2-intel-shmem
mvapich-1.2-pgi
mvapich-1.2-pgi-psm
mvapich-1.2-pgi-shmem
mvapich2-1.7-intel
mvapich2-1.7-intel-psm
mvapich2-1.7-intel-shmem
mvapich2-1.7-pgi
mvapich2-1.7-pgi-psm
mvapich2-1.7-pgi-shmem
netcdf-4.1-intel
openmpi-1.4-intel
openmpi-1.4-pgi
openmpi-1.5-intel
openmpi-1.5-pgi
openmpi-1.6-intel
openmpi-1.6-pgi
pathscale-3.2
pgi-12.5
pgi-8.0
dts