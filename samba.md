## Install things

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

