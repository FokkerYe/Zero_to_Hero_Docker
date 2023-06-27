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






