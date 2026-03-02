As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file /opt/docker/Dockerfile (please keep D capital of Dockerfile) on App server 1 in Stratos DC and configure to build an image with the following requirements:

a. Use ubuntu:24.04 as the base image.

b. Install apache2 and configure it to work on 5001 port. (do not update any other Apache configuration settings like document root etc).

Solution:

[root@stapp01 docker]# cat Dockerfile 

FROM ubuntu:24.04

RUN apt update -y && apt install apache2 -y && sed -i 's/Listen 80/Listen 5001/' /etc/apache2/ports.conf

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

The primary purpose of running a process in the foreground within a Docker container is to keep the container "alive". Docker containers only run as long as the main process (PID 1) is active. If Apache were started in the background (daemon mode), the initial process would exit immediately, causing the container to stop. Running it in the foreground ensures the container persists and also allows its logs to be streamed directly to the Docker standard output and error streams


[root@stapp01 docker]# docker build -t apache .

[root@stapp01 docker]# docker run -d -p 80:5001 apache

[root@stapp01 docker]# curl stapp01:80


