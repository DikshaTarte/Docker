# Docker
MFS088@MFS088 MINGW64 ~/Downloads (main)
$ ssh -i "MyDockerKey13Oct2023.pem" ubuntu@ec2-18-222-232-88.us-east-2.compute.amazonaws.com

ubuntu@ip-172-31-42-149:~$ sudo -i

root@ip-172-31-42-149:~# apt-get update

root@ip-172-31-42-149:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

root@ip-172-31-42-149:~# docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

root@ip-172-31-42-149:~# ls
install-docker.sh  snap

root@ip-172-31-42-149:~# vi mydockerfile

root@ip-172-31-42-149:~# ls
install-docker.sh  mydockerfile  snap

root@ip-172-31-42-149:~# rm -r mydockerfile

root@ip-172-31-42-149:~# ls
install-docker.sh  snap

root@ip-172-31-42-149:~# vi Dockerfile
FROM ubuntu:22.04
MAINTAINER diksha
RUN apt-get update
CMD ["echo","This is my first container"]
:wq!

root@ip-172-31-42-149:~# ls
Dockerfile  install-docker.sh  snap

root@ip-172-31-42-149:~# docker build -t myimage:1 .

root@ip-172-31-42-149:~# ls
Dockerfile  install-docker.sh  snap

root@ip-172-31-42-149:~# vi Dockerfile

root@ip-172-31-42-149:~# docker build -t myimage:1 .
[+] Building 7.7s (6/6) FINISHED                                 docker:default
 => [internal] load build definition from Dockerfile                       0.0s
 => => transferring dockerfile: 136B                                       0.0s
 => [internal] load .dockerignore                                          0.0s
 => => transferring context: 2B                                            0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04            0.5s
 => [1/2] FROM docker.io/library/ubuntu:22.04@sha256:2b7412e6465c3c7fc5bb  2.3s
 => => resolve docker.io/library/ubuntu:22.04@sha256:2b7412e6465c3c7fc5bb  0.0s
 => => sha256:2b7412e6465c3c7fc5bb21d3e6f1917c167358449fe 1.13kB / 1.13kB  0.0s
 => => sha256:c9cf959fd83770dfdefd8fb42cfef0761432af36a764c07 424B / 424B  0.0s
 => => sha256:e4c58958181a5925816faa528ce959e487632f4cfd1 2.30kB / 2.30kB  0.0s
 => => sha256:aece8493d3972efa43bfd4ee3cdba659c0f787f8f 29.54MB / 29.54MB  0.4s
 => => extracting sha256:aece8493d3972efa43bfd4ee3cdba659c0f787f8f59c82fb  1.7s
 => [2/2] RUN apt-get update                                               4.4s
 => exporting to image                                                     0.3s
 => => exporting layers                                                    0.3s
 => => writing image sha256:c0c3ff34d04f86471ee7764cb4cc0edb0f2f07d15e5ce  0.0s
 => => naming to docker.io/library/myimage:1                               0.0s
 
root@ip-172-31-42-149:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
myimage      1         c0c3ff34d04f   11 seconds ago   122MB

root@ip-172-31-42-149:~# docker run myimage:1
This is my first container

root@ip-172-31-42-149:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

root@ip-172-31-42-149:~# docker ps -a
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS                      PORTS     NAMES
9d8264066c66   myimage:1   "echo 'This is my fi…"   15 seconds ago   Exited (0) 14 seconds ago             wizardly_taussig


root@ip-172-31-42-149:~# docker build -t myimage:2 .
[+] Building 0.3s (6/6) FINISHED                                                                           docker:default
 => [internal] load build definition from Dockerfile                                                                 0.0s
 => => transferring dockerfile: 148B                                                                                 0.0s
 => [internal] load .dockerignore                                                                                    0.0s
 => => transferring context: 2B                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04                                                      0.2s
 => [1/2] FROM docker.io/library/ubuntu:22.04@sha256:2b7412e6465c3c7fc5bb21d3e6f1917c167358449fecac8176c6e496e5c1f0  0.0s
 => CACHED [2/2] RUN apt-get update                                                                                  0.0s
 => exporting to image                                                                                               0.0s
 => => exporting layers                                                                                              0.0s
 => => writing image sha256:ecc1d5ae64e7aebe2ea2abfb3e24176590979eebbd5e8168f4eddccaae8f065b                         0.0s
 => => naming to docker.io/library/myimage:2                                                                         0.0s


root@ip-172-31-42-149:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
myimage      1         c0c3ff34d04f   2 hours ago   122MB
myimage      2         ecc1d5ae64e7   2 hours ago   122MB

root@ip-172-31-42-149:~# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

root@ip-172-31-42-149:~# docker ps -a
CONTAINER ID   IMAGE       COMMAND                  CREATED       STATUS                   PORTS     NAMES
9d8264066c66   myimage:1   "echo 'This is my fi…"   2 hours ago   Exited (0) 2 hours ago             wizardly_taussig

root@ip-172-31-42-149:~# docker ps -la
CONTAINER ID   IMAGE       COMMAND                  CREATED       STATUS                   PORTS     NAMES
9d8264066c66   myimage:1   "echo 'This is my fi…"   2 hours ago   Exited (0) 2 hours ago             wizardly_taussig

