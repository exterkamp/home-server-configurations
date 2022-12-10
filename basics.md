

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

I usually turn off SSL. `SHELLINABOX_ARGS="--no-beep --disable-ssl"`

Now you can use the terminal from the browser @ port 4200.
