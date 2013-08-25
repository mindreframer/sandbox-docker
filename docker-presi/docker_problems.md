docker problem:
hostname: Name or service not known


- http://ubuntuforums.org/archive/index.php/t-1467978.html
- http://www.rootforum.org/forum/viewtopic.php?f=148&t=50810



1. docker run -dns 8.8.8.8 -dns 8.8.4.4 ...
2. change

/etc/hostname: some-md5-number
/etc/hosts: 127.0.0.1 some-md5-number.meinedomain.de some-md5-number

-> `hostname -f` will work again


Docker mounts /etc/resolv.conf from the host system as read-only file into the container:
https://github.com/dotcloud/docker/blob/master/lxc_template.go#L84

to change it, start docker with  `-dns` params.



To have puppet working properly, you have to install net-tools:

apt-get install net-tools



docker run -dns 8.8.8.8 -dns 8.8.4.4 -h=puppet-test -i -t my/base bash

> nano + net-tools




docker run -dns 8.8.8.8 -dns 8.8.4.4 -h=puppet-test -i -t my/puppet-omnibus bash
