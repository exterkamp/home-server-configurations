

## Shell in a box

```sh
# install
$ sudo apt-get install shellinabox

# get status
$ /etc/init.d/shellinabox status

# edit settings
$ nano /etc/default/shellinabox

# restart
$ /etc/init.d/shellinabox restart
```

You can do things like turn off SSL. `SHELLINABOX_ARGS="--no-beep --disable-ssl"`

Now you can use the terminal from the browser @ port 4200.

## Portainer

https://docs.portainer.io/start/install/server/docker/linux

```sh
# Pull the image!
$ docker volume create portainer_data

$ docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

Now you can go to portainer @ port 9443.

## Homer

https://github.com/bastienwirtz/homer

I make a homer dir in my user files `/home/shane/code/homer/assets/` then plug that into homer.

```sh
$ docker run -d -p 8084:8080 -v /home/shane/code/homer/assets:/www/assets --user 1000:1000 --restart=always --name homer  b4bz/homer:latest
```

## Linux-dash

```sh
$ docker run -d -p 9250:80 --restart=always --name dashboard alysivji/linux-dash
```

## code-server

I have my code setup in `/home/shane/code` so we put that into the `git` volume.

```sh
$ docker run -d --name=code-server -e PUID=1000 -e PGID=1000 -e TZ=America/Los_Angeles -p 8443:8443 -v /home/shane/appdata/config:/config -v /home/shane/code:/git --restart unless-stopped lscr.io/linuxserver/code-server:latest
```
