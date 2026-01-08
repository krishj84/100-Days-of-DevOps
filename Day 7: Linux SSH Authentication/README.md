Day 7: Linux SSH Authentication

The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1). Based on the requirements, perform the following:

Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.


The ssh-keygen command generates a public/private key pair used for secure, passwordless authentication between systems. The public key is placed on the server you want to access, while the private key remains securely on your local machine. 

Command: ssh-keygen -t rsa

Copy the Public Key: Copy the contents of the .pub file and add it to the remote server's ~/.ssh/authorized_keys file
