# Transmission on Alpine Linux
[![](https://badge.imagelayers.io/ccorsano/alpine-transmission:latest.svg)](https://imagelayers.io/?images=ccorsano/alpine-transmission:latest 'Get your own badge on imagelayers.io')

## docker-transmission

Transmission Daemon Docker Container
Very basic fork of rlesouef/alpine-transmission to allow persistence of the config files using a shared volume.

Try it out
----------

Change transmission-daemon config:

    docker run -ti ccorsano/alpine-transmission vi /etc/transmission-daemon/settings.json

Create:

    mkdir -p /var/transmission/{downloads,incomplete}

Run the container:

    docker run -d --name transmission \
    -p 9091:9091 \
    -p 51413:51413/tcp \
    -p 51413:51413/udp \
    -e "USERNAME=admin" \
    -e "PASSWORD=password" \
    -v /var/transmission/downloads:/transmission/downloads \
    -v /var/transmission/incomplete:/transmission/incomplete \
    ccorsano/alpine-transmission

Connect to running container::

    docker exec -ti _name_container_ /bin/sh

Build it yourself
-----------------

    git clone https://github.com/ccorsano/alpine-transmission.git
    cd alpine-transmission
    docker build -t ccorsano/alpine-transmission .


```
mkdir -p /data/username/transmission/{downloads,incomplete,config}
```

Application container, don't forget to specify a password for `transmission` account and local directory for the downloads:

```
docker run -d  --name transmission \
-p 51413:51413 -p 51413:51413/udp -p 9091:9091 \
-v /data/username/transmission/downloads:/torrents/downloads \
-v /data/username/transmission/incomplete:/torrents/incomplete \
-v /data/username/transmission/config:/etc/transmission-daemon \
ccorsano/alpine-transmission

```
