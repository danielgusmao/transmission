# Transmission on Alpine Linux
![](http://idroot.net/wp-content/uploads/2015/02/transmission-bittorrent.jpg)

## docker-transmission
----------------------------------
This project has been copied from.

https://github.com/ccorsano/alpine-transmission

https://hub.docker.com/r/ccorsano/alpine-transmission/

and is being modified by me.
----------------------------------

Transmission Daemon Docker Container
Very basic fork of rlesouef/alpine-transmission to allow persistence of the config files using a shared volume.

Try it out
----------

Create:

    mkdir -p /var/transmission/{downloads,incomplete}

Run the container:

    docker run -d --name transmission \
    -p 9091:9091 \
    -p 51413:51413/tcp \
    -p 51413:51413/udp \
    -v /var/transmission/downloads:/transmission/downloads \
    -v /var/transmission/incomplete:/transmission/incomplete \
    danielgusmao/transmission

Connect to running container::

    docker exec -it name_container /bin/sh

Build it yourself
-----------------

    git clone https://github.com/danielgusmao/transmission
    cd transmission
    docker build -t YourUserName/transmission .

