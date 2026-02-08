The Nautilus DevOps team is conducting application deployment tests on selected application servers. They require a nginx container deployment on Application Server 2. Complete the task with the following instructions:

On Application Server 2 create a container named nginx_2 using the nginx image with the alpine tag. Ensure container is in a running state.

Solution:

docker run -d --name nginx_2 nginx:alpine

docker ps

<img width="1496" height="768" alt="image" src="https://github.com/user-attachments/assets/55af1bf2-4a0a-48ba-9807-5581f3f5d595" />
