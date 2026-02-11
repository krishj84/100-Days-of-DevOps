One of the Nautilus developer was working to test new changes on a container. He wants to keep a backup of his changes to the container. A new request has been raised for the DevOps team to create a new image from this container. Below are more details about it:

a. Create an image ecommerce:xfusion on Application Server 3 from a container ubuntu_latest that is running on same server.


Solution:

docker ps

docker commit [OPTIONS] CONTAINER_NAME_OR_ID REPOSITORY:TAG

docker commit ubuntu_latest ecommerce:xfusion

<img width="1460" height="608" alt="image" src="https://github.com/user-attachments/assets/44d93f86-eb13-45b3-8ea5-90830e30b5aa" />
