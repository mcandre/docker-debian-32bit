# docker-debian-32bit - Docker base images for 32bit Debian

# ABOUT

docker-debian-32bit is a collection of [debootstrap](https://wiki.debian.org/Debootstrap)-generated 32-bit Debian base images.

# DOCKER HUB

https://registry.hub.docker.com/u/mcandre/docker-debian-32bit/

# EXAMPLE

```
$ make
docker run --rm --privileged -v $(pwd):/mnt -t debian:sid sh -c 'apt-get update && apt-get install -y debootstrap && mkdir /chroot && debootstrap --arch i386 sid /chroot && cd /chroot && tar czvf /mnt/rootfs.tar.gz .'
...

docker build -t mcandre/docker-debian-32bit:latest .
Step 0 : FROM scratch
Step 1 : MAINTAINER Andrew Pennebaker <andrew.pennebaker@gmail.com>
Step 2 : ADD rootfs.tar.gz /
Successfully built 5ac6b04a4424

docker run --rm mcandre/docker-debian-32bit:latest sh -c 'cat /etc/*release*'
PRETTY_NAME="Debian GNU/Linux stretch/sid"
NAME="Debian GNU/Linux"
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support/"
BUG_REPORT_URL="https://bugs.debian.org/"
```

# REQUIREMENTS

* [Docker](https://www.docker.com/)

## Optional

* [make](http://www.gnu.org/software/make/)
* [Node.js](https://nodejs.org/en/) (for dockerlint)
