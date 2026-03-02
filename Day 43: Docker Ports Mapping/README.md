The Nautilus DevOps team is planning to host an application on a nginx-based container. There are number of tickets already been created for similar tasks. One of the tickets has been assigned to set up a nginx container on Application Server 3 in Stratos Datacenter. Please perform the task as per details mentioned below:

a. Pull nginx:stable docker image on Application Server 3.

b. Create a container named games using the image you pulled.

c. Map host port 6400 to container port 80. Please keep the container in running state.

Solution:

[root@stapp03 banner]# docker pull nginx:stable

[root@stapp03 banner]# docker run -d --name games -p 6400:80 nginx:stable 

cfec35e5fff060145d2ecd77dde3a741dfa67abff0f86316511b6b2b3f49cc50

[root@stapp03 banner]# curl stapp03:6400


