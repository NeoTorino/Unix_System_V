# Unix_System_V
AT&amp;T Unix System V Release 4 Version 2.1

---------------------------------------

|   |   |
| ------------- | ------------- |
| Version | Release 4 Version 2.1 |
| Language | English |
| Processor architecture | x86-32 |
| File type | 3½ Floppy |
| File size | 5.84MB |

# Installation (using qemu)

Hard Drive contains a fresh installation.
It has been divided in files of 50M. Total size is 200M

```
$ qemu-img create -f raw sysv.img 200M
```

Boot from floppy disk
```
qemu-system-i386 -boot a -drive file=./sysv.img,format=raw,if=ide -drive file=../ATT_UNIX_System_V_Release_4_Version_2.1-3/Base_01_2.1a.img,format=raw,if=floppy
```

If you are using linux you can add "-accel kvm" flag to speed up qemu: $ qemu-system-i386 -hda sysv.img -fda floppy/Base_01\_\(2.1a\).img -boot a -accel kvm

To change floppy during installation, press Ctrl+Alt+2, and enter 
```

$ change floppy0 ../ATT_UNIX_System_V_Release_4_Version_2.1-3/Base_02_2.1a.img raw
```
Press Ctrl+Alt+1 back to VM's vga
Repeat this step for the 10 ('Base') floppy disks

After being asked to reboot the first time after floppy Base02, close the windown and run:
```
$ qemu-system-i386 -boot c -drive file=./sysv.img,format=raw,if=ide -drive file=./Base_03.img,format=raw,if=floppy
```

And press:
```
F
```


After installation you can boot SystemV using
```
$ qemu-system-i386 -hda sysv.img  # or "$ qemu-system-i386 -hda sysv.img -accel kvm" if you are using linux.
```

# A new disk has been created after installation and split in pieces of 50MB.

# To ucompress the tar.gz run:
```
tar -xvzf ATT_UNIX_System_V_Release_4_Version_2.1-3.tar.gz
```

sha256 ATT_UNIX_System_V_Release_4_Version_2.1-3.tar.gz
`10a68bac3180ac09d99088688efb691076dc00f1e72b6546b2456c829ae5e3c5`

sha512 ATT_UNIX_System_V_Release_4_Version_2.1-3.tar.gz
`768ebf709b1c5eab552fa517d731c38226ae562885e7ce138b9982827285e0eed2842b16b87fc171a20de208f35c159499d0a6a71f8173a7b912709c75bcb57e`


To concatenate the files:
```
$ cat sysv.img_part* > sysv.img
```

Default password for root/user/services is: changeme

The hard drive has been split with the following command (on FreeBSD):
```
$ split -b 50M -d sysv.img sysv.img_part
```

# Add additional packages using:
```
$ pkgadd -d diskette1
```
