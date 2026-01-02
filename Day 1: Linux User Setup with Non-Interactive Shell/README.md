https://lnkd.in/gwqn8yJ9 

Day 1: Linux User Setup with Non-Interactive Shell

Question: Create a user named rose with a non-interactive shell on App Server 1

A Non-interactive shell in Linux is an account configured for automated tasks or services that does not allow a person to login and issue commands manually.

Command:
ssh user@AppServer1
sudo useradd -s /sbin/nologin rose
