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

