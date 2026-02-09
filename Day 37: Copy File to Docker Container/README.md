The Nautilus DevOps team possesses confidential data on App Server 1 in the Stratos Datacenter. A container named ubuntu_latest is running on the same server.

Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /home/. Ensure the file is not modified during this operation.

Solution:

docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/home/

docker exec -it ubuntu_latest ls -l /home/

<img width="1716" height="590" alt="image" src="https://github.com/user-attachments/assets/118331d4-28e6-4006-b5fb-aeb96429edd0" />



