One of the Nautilus DevOps team members was working to configure services on a kkloud container that is running on App Server 3 in Stratos Datacenter. Due to some personal work he is on PTO for the rest of the week, but we need to finish his pending work ASAP. Please complete the remaining work as per details given below:

a. Install apache2 in kkloud container using apt that is running on App Server 3 in Stratos Datacenter.

b. Configure Apache to listen on port 5002 instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on localhost, 127.0.0.1, container ip, etc.

c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

Solution:

[root@stapp03 banner]# docker ps

CONTAINER ID   IMAGE          COMMAND       CREATED         STATUS         PORTS     NAMES

153af9672928   ubuntu:18.04   "/bin/bash"   2 minutes ago   Up 2 minutes             kkloud

[root@stapp03 banner]# docker exec -it 153a bash

root@153af9672928:/# cat /etc/os-release  
NAME="Ubuntu"

Install apt/apache2/vim packages

  apt update -y

  apt install apache2 -y

  apt install vim -y

Update the port in ports.conf under /etc/apache2

Start the apache2 service --> service apache2 start

Test the url : curl://localhost:5002

