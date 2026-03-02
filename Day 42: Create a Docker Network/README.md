The Nautilus DevOps team needs to set up several docker environments for different applications. One of the team members has been assigned a ticket where he has been asked to create some docker networks to be used later. Complete the task based on the following ticket description:

a. Create a docker network named as media on App Server 3 in Stratos DC.

b. Configure it to use bridge drivers.

c. Set it to use subnet 192.168.0.0/24 and iprange 192.168.0.0/24.

Solution:

[root@stapp03 banner]# docker network create --driver bridge --subnet 192.168.0.0/24 --ip-range 192.168.0.0/24 media

9b25494b6aa8bce834908bf08999c66124ff69bb4684b2e8041fa18f003c30e6

<img width="1586" height="490" alt="image" src="https://github.com/user-attachments/assets/a061fbf4-1481-482a-b578-9e7e176c1677" />

[root@stapp03 banner]# docker network inspect media



