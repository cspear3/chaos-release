#FAQ

#Questions and answers to things we get asked.

**Q: Where can I download CHAOS?**
> A: [ftp://gdo-lc.ucllnl.org/pub/projects/chaos](ftp://gdo-lc.ucllnl.org/pub/projects/chaos)

**Q: I have chaos installed how can I update it?**
> A: `sudo yum -c ftp://gdo-lc.ucllnl.org/pub/projects/chaos/chaos.centos.repo --enablerepo=4.4* update`

**Q: How do I get a list of YUM groups?**
> A: `sudo yum -c ftp://gdo-lc.ucllnl.org/pub/projects/chaos/chaos.centos.repo --disablerepo=* --enablerepo=4.4* grouplist`

**Q: How do I install a YUM group?**
> A: `yum -c ftp://gdo-lc.ucllnl.org/pub/projects/chaos/chaos.centos.repo --disablerepo=* --enablerepo=4.4* groupinstall YUM_GROUP`

> where YUM\_GROUP is the group you want.

**Q: I see you have a nvidia rpm, how do I make that work?**
> A: Add to the beginning of ld.so.conf:
```
/usr/nvidia/lib
/usr/nvidia/lib64
```
> run `ldconfig` and in /etc/X11/xorg.conf add
```
Section "Files"
    ModulePath      "/usr/nvidia/X11R6/lib/modules"
    ModulePath      "/usr/lib64/xorg/modules"
    ModulePath      "/usr/X11R6/lib64/modules"
    FontPath        "unix/:7100"
EndSection
```
> and in the Device section of xorg.conf change your Driver to
```
    Driver          "nvidia"
```