---
description: This page will just describing the linux file system
---

# File System Structure

```
/boot - Contains file that is used by the boot loader (grub.cfg)
/root - root user home directory. It is not same as / 
/dev - system devices (e.g. disk, cdrom, speakers, flashdrive, keyboard etc.)
/etc - Configuration files 
/bin -> /usr/bin - Everyday user commands 
/sbin -> /usr/bin - System/filesystem commands 
/opt - Optional add-on applications (Not part of OS apps)
/proc - Running processes (Only exist in Memory)
/lib -> usr/lib - C Programming library files by commands and apps 

/tmp - Directory for temp files 
/home - Directory for user 
/var - System logs
/run - System daemons that start very early (e.g. systemd and udev) to store temporary
runtime files like PID files
/mnt - To mount an external filesystem (e.g. NFS)
/media - For cdrom mounts
```
