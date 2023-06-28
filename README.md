# Zero_to_Hero_Docker

```
docker -v 
docker images 
```
Output
$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
[node1] (local) root@192.168.0.8 ~

```
 docker pull alpine
````
Output
$ docker pull alpine
Using default tag: latest
latest: Pulling from library/alpine
31e352740f53: Pull complete 
Digest: sha256:82d1e9d7ed48a7523bdebc18cf6290bdb97b82302a8a9c27d4fe885949ea94d1
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest
[node1] (local) root@192.168.0.8 
```
 docker pull ubuntu:latest
```
output
root@ubuntu-22-04:~# docker pull ubuntu:latest
latest: Pulling from library/ubuntu
6b851dcae6ca: Pull complete
Digest: sha256:6120be6a2b7ce665d0cbddc3ce6eae60fe94637c6a66985312d1f02f63cc0bcd
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
root@ubuntu-22-04:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
alpine       latest    c1aabb73d233   12 days ago   7.33MB
ubuntu       latest    99284ca6cea0   3 weeks ago   77.8MB
root@ubuntu-22-04:~#
```
docker pull image_name:tag
docker images
docker rmi image_name (or)
docker rmi image_id (or)
docker rm remove image_name (or)image_ID
docker images -q
docker rmi $(docker images -q)-f
```
output
root@ubuntu-22-04:~# docker images
REPOSITORY       TAG       IMAGE ID       CREATED         SIZE
alpine           latest    c1aabb73d233   12 days ago     7.33MB
ubuntu           latest    99284ca6cea0   3 weeks ago     77.8MB
circleci/mysql   latest    9e8d77206977   16 months ago   519MB
root@ubuntu-22-04:~# docker rmi circleci/mysql
Untagged: circleci/mysql:latest
Untagged: circleci/mysql@sha256:b8aabed03a3c72f4aa1501a565c7a0d87dd3e53ab84dca8d                                                                                                             a41c78cb0ca8eb78
Deleted: sha256:9e8d772069776d016a447ac629a34271e2d4e8b4c87fbe94e3ba5610d2560403
Deleted: sha256:36aec3689394b4c4257e3283e9baaab67124ea31be8d74dfdebf3d9ba8be1971
Deleted: sha256:10bf39a24625d39d92249386510885f15b705a5da74945f98256fd0817fe7eb5
Deleted: sha256:1667cf286d930e8ffb90f90db8b2a059a02bafd3c6f70e8e565d69c3e4abe34e
Deleted: sha256:8f3d1a0a2d4178c0fede3eaa19f33d320209f46ef7268d97cebb590a8985264d
Deleted: sha256:cc08389d540a702be5110a2147430d0b4c935119e53a737e1d8a1d2f43bba038
Deleted: sha256:f9987717a989ba21aee0a3ef5b1189a507eb393aa0e88de58435357b3ec6dd92
Deleted: sha256:c5a578662a7c39216cc7832bb64b81ada6bc73c639effa8117f223672ea9aba0
Deleted: sha256:156aa1a11e93325c2fc2303736d7902a0be9ad4b29d30561ab6b12050ad12f46
Deleted: sha256:6a4d005549c580ebf87f192fdcfb1c9dfd91f4ff6b934d284c9cb49f2af13fd5
Deleted: sha256:59fc12d50d81beac733e8069de09b0d8f05f518783076d0a11082fff76535355
Deleted: sha256:a85e24ac4d077fd96f02199a49127739f0e9ad1299bea356e33e96e7a59327d3
Deleted: sha256:c463c437c67d8fe9ae10b80b84128e5673032a2f0f5951956b2da99160623533
Deleted: sha256:f18b02b14138b6f9808f9843cc645e2edd64b02ca1c87e671355f56d1b4b5ec6
root@ubuntu-22-04:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
alpine       latest    c1aabb73d233   12 days ago   7.33MB
ubuntu       latest    99284ca6cea0   3 weeks ago   77.8MB
root@ubuntu-22-04:~#
`````
docker run -<option> <image>:<tag>
docker ru -d -it ubuntu:latest
docker ps
docker exec -it <docker id> <shell>
```
output

root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~#
```
docker run -it alpine
```
output
root@ubuntu-22-04:~# docker run -it alpine
/ # cat /etc/*-release
3.18.2
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.18.2
PRETTY_NAME="Alpine Linux v3.18"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
/ #
```
docker run -d -it alpine
```

output
root@ubuntu-22-04:~# docker run -d -it alpine
8ff105a742e1fb954898a5c73c7031e87907fc368d8baff37a220c990f7214c0
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS        PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   3 seconds ago   Up 1 second             recursing_hermann
root@ubuntu-22-04:~#
```
docker exec -it 8ff sh
```
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS         PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   3 minutes ago   Up 3 minutes             recursing_hermann
root@ubuntu-22-04:~# docker exec -it 8ff sh
/ # cat /etc/*-release
3.18.2
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.18.2
PRETTY_NAME="Alpine Linux v3.18"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
/ #
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS         PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   5 minutes ago   Up 5 minutes             recursing_hermann
root@ubuntu-22-04:~# docker exec -it 8ff sh
/ # ps -x
ps: unrecognized option: x
BusyBox v1.36.1 (2023-06-02 00:42:02 UTC) multi-call binary.

Usage: ps [-o COL1,COL2=HEADER] [-T]

Show list of processes

        -o COL1,COL2=HEADER     Select columns for display
        -T                      Show threads
/ # ps
PID   USER     TIME  COMMAND
    1 root      0:00 /bin/sh
   18 root      0:00 sh
   24 root      0:00 ps
```
docker stop 8ff
```
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS         PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   9 minutes ago   Up 9 minutes             recursing_hermann
root@ubuntu-22-04:~# docker stop 8ff
8ff
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~#
output
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND     CREATED          STATUS                       PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   14 minutes ago   Exited (137) 4 minutes ago             recursing_hermann
edda8974739d   alpine    "/bin/sh"   18 minutes ago   Exited (0) 17 minutes ago              inspiring_euler
```
docker run --name alpine -it alpine
```
output
root@ubuntu-22-04:~#
root@ubuntu-22-04:~# docker run --name alpine -it alpine
/ # cd /tmp/
/tmp # ls
/tmp # echo "hello docker" >ayk.txt
/tmp # cat ayk.txt
hello docker
/tmp # exit

output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~# docker exec -d -it 16bca159c4a2 sh
Error response from daemon: Container 16bca159c4a2245b395e5df392375a6a4c9fa7609d18a170eebd6ce5eae1edbb is not running
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND     CREATED          STATUS                        PORTS     NAMES
16bca159c4a2   alpine    "/bin/sh"   5 minutes ago    Exited (0) 4 minutes ago                alpine
8ff105a742e1   alpine    "/bin/sh"   21 minutes ago   Exited (137) 10 minutes ago             recursing_hermann
edda8974739d   alpine    "/bin/sh"   24 minutes ago   Exited (0) 23 minutes ago               inspiring_euler
root@ubuntu-22-04:~# docker start 16b
16b
root@ubuntu-22-04:~# docker exec -it 16b sh
/ # cd /tmp
/tmp # ls
ayk.txt
/tmp # cat ayk.txt
hello docker
/tmp #
```
 docker rm alpine
```
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS         PORTS     NA                                                                                                             MES
16bca159c4a2   alpine    "/bin/sh"   7 minutes ago   Up 2 minutes             al                                                                                                             pine
root@ubuntu-22-04:~# docker stop 16b
16b
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND     CREATED          STATUS                                                                                                                                     PORTS     NAMES
16bca159c4a2   alpine    "/bin/sh"   8 minutes ago    Exited (137) 8 seconds ago                                                                                                                           alpine
8ff105a742e1   alpine    "/bin/sh"   24 minutes ago   Exited (137) 13 minutes ag                                                                                                             o             recursing_hermann
edda8974739d   alpine    "/bin/sh"   27 minutes ago   Exited (0) 26 minutes ago                                                                                                                            inspiring_euler
root@ubuntu-22-04:~# docker rm alpine
alpine
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND     CREATED          STATUS                                                                                                                                     PORTS     NAMES
8ff105a742e1   alpine    "/bin/sh"   24 minutes ago   Exited (137) 14 minutes ag                                                                                                             o             recursing_hermann
edda8974739d   alpine    "/bin/sh"   28 minutes ago   Exited (0) 27 minutes ago                                                                                                                            inspiring_euler
root@ubuntu-22-04:~#
```
docker run alpine /etc/os-release
```
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~# docker run alpine whoami
root
root@ubuntu-22-04:~# docker run alpine /etc/os-release
docker: Error response from daemon: failed to create shim task: OCI runtime crea                                                                                                             te failed: runc create failed: unable to start container process: exec: "/etc/os                                                                                                             -release": permission denied: unknown.
root@ubuntu-22-04:~# docker run alpine cat /etc/os-release
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.18.2
PRETTY_NAME="Alpine Linux v3.18"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
root@ubuntu-22-04:~#
```
docker run -dit alpine
docker stats ff8
```
output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~# docker run -dit alpine
ff866718263233d52320a761cc03349c5a57f6704fb19adfd5729236b0ffb953
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED         STATUS         PORTS     NA                                                                                                             MES
ff8667182632   alpine    "/bin/sh"   6 seconds ago   Up 5 seconds             be                                                                                                             autiful_pike
root@ubuntu-22-04:~# docker stats ff8
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT   MEM %     NET I/O                                                                                                                    BLOCK I/O   PIDS
ff8667182632   beautiful_pike   0.00%     364KiB / 1.93GiB    0.02%     1.02kB /                                                                                                              0B   0B / 0B     1
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT   MEM %     NET I/O                                                                                                                    BLOCK I/O   PIDS
ff8667182632   beau
```
docker stats --all --format "table {{.Container}}\t{{.CPUPerc}}\t {{.MemUsage}}" ff8
```

output
root@ubuntu-22-04:~# docker stats --all --format "table {{.Container}}\t{{.CPUPerc}}\t {{.MemUsage}}" ff8
CONTAINER   CPU %      MEM USAGE / LIMIT
ff8         0.00%      364KiB / 1.93GiB
CONTAINER   CPU %      MEM USAGE / LIMIT
ff8         0.00%      364KiB / 1.93GiB
CONTAINER   CPU %      MEM USAGE / LIMIT
ff8         0.00%      364KiB / 1.93GiB
CONTAINER
```
docker container stop ff8
docker container rm ff8
```


output
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND     CREATED       STATUS       PORTS     NAMES
ff8667182632   alpine    "/bin/sh"   3 hours ago   Up 3 hours             beauti                                                                                                             ful_pike
root@ubuntu-22-04:~# docker container stop ff8
ff8
root@ubuntu-22-04:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND                 CREATED       STATUS                        PORTS     NAMES
ff8667182632   alpine    "/bin/sh"               3 hours ago   Exited (137) 35 seconds ago             beautiful_pike
459467688e4e   alpine    "cat /etc/os-release"   3 hours ago   Exited (0) 3 hours ago                  cool_yonath
af5b53d4c6d8   alpine    "/etc/os-release"       3 hours ago   Created                                 recursing_noether
7094af0bb524   alpine    "whoami"                3 hours ago   Exited (0) 3 hours ago                  mystifying_noether
8ff105a742e1   alpine    "/bin/sh"               3 hours ago   Exited (137) 3 hours ago                recursing_hermann
edda8974739d   alpine    "/bin/sh"               3 hours ago   Exited (0) 3 hours ago                  inspiring_euler
root@ubuntu-22-04:~# docker container rm ff8
ff8
root@ubuntu-22-04:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND                 CREATED       STATUS                     PORTS     NAMES
459467688e4e   alpine    "cat /etc/os-release"   3 hours ago   Exited (0) 3 hours ago               cool_yonath
af5b53d4c6d8   alpine    "/etc/os-release"       3 hours ago   Created                              recursing_noether
7094af0bb524   alpine    "whoami"                3 hours ago   Exited (0) 3 hours ago               mystifying_noether
8ff105a742e1   alpine    "/bin/sh"               3 hours ago   Exited (137) 3 hours ago             recursing_hermann
edda8974739d   alpine    "/bin/sh"               3 hours ago   Exited (0) 3 hours ago               inspiring_euler
root@ubuntu-22-04:~#

output

ubuntu       latest    99284ca6cea0   3 weeks ago   77.8MB
root@ubuntu-22-04:~# docker run -it --name=web -p 80:80 ubuntu:20.04
`
``
root@ubuntu-22-04:~# cat Dockerfile
FROM ubuntu:20.04
MAINTAINER AYK
RUN apt-get update && apt-get install -y tzdata && apt-get install -y apache2
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
EXPOSE 80
CMD ["apache2ctl", "-D", "FOREGROUND"]
root@ubuntu-22-04:~#

 docker build -t apache2 .
docker run -d --name aykweb1 -p 80:60 apache2
```
output
https://github.com/konova-mm/static_page
root@ubuntu-22-04:~/static_page# cat Dockerfile
FROM ubuntu:18.04
LABEL maintainer="konova@novaitg.com"
ENV REFRESHED_AT 2021-12-12
RUN apt-get -yqq update; apt-get -yqq install nginx

ADD index.html /var/www/html/index.html
ADD style.css /var/www/html/style.css

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
EXPOSE 80
root@ubuntu-22-04:~/static_page#

 docker build -t static_page .
 docker run -d -p 80:800 --name static_web static_page
```
















