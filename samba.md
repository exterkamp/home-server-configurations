## Install things

List the drives:

```sh
$ lsblk
pi@raspberry:~ $ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    1 58.6G  0 disk
└─sda1        8:1    1 58.6G  0 part
sdb           8:16   1  7.2G  0 disk
└─sdb1        8:17   1  7.2G  0 part /media/yellow_usb
mmcblk0     179:0    0 14.8G  0 disk
├─mmcblk0p1 179:1    0  256M  0 part /boot
└─mmcblk0p2 179:2    0 14.6G  0 part /
```

Using exfat drives?

```sh
$ sudo apt-get install exfat-fuse exfat-utils
```

### Mount a drive

```sh
$ sudo mount -t exfat /dev/sda1 /media/xxx
```

unmount

```sh
$ sudo umount /dev/sda1 
```

list devices

```sh
$ mount -v | grep '/dev/sd'
```

## Configuration

```sh
$ sudo nano /etc/samba/smb.conf
```

Add a configuration for the drive in the samba config.

```sh
[yellow_usb]
path = /media/yellow_usb
writeable=Yes
create mask=0777
directory mask=0777
public=no
```

And set a samba user.

```sh
$ sudo smbpasswd -a pi
```

```sh
$ sudo systemctl restart smbd
```


## Mkdirs

I usually mount drives in directories in `/media/` and name them describing which drive they are...

```
$ mkdir /media/yellow_usb
```

## Check status

```sh
$ sudo smbstatus --shares
pi@raspberry:~ $ sudo smbstatus --shares

Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------
yellow_usb   2509    192.168.0.3   Sun Jan  1 19:37:27 2023 PST     -            -
IPC$         2509    192.168.0.3   Sun Jan  1 19:37:24 2023 PST     -            -
```
