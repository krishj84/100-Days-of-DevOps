Nautilus project developers are planning to start testing on a new project. As per their meeting with the DevOps team, they want to test containerized environment application features. As per details shared with DevOps team, we need to accomplish the following task:

a. Pull busybox:musl image on App Server 2 in Stratos DC and re-tag (create new tag) this image as busybox:media.

Solution:

docker pull busybox:musl

docker tag busybox:musl busybox:media

docker images

<img width="1460" height="578" alt="image" src="https://github.com/user-attachments/assets/278e34c6-d84f-4c3f-8297-47adfc4e3c1a" />

