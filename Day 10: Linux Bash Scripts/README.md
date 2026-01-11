The production support team of xFusionCorp Industries is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on App Server 1 in Stratos Datacenter, and they need to create a bash script named ecommerce_backup.sh which should accomplish the following tasks. (Also remember to place the script under /scripts directory on App Server 1).

a. Create a zip archive named xfusioncorp_ecommerce.zip of /var/www/html/ecommerce directory.

b. Save the archive in /backup/ on App Server 1. This is a temporary storage, as backups from this location will be clean on weekly basis. Therefore, we also need to save this backup archive on Nautilus Backup Server.

c. Copy the created archive to Nautilus Backup Server server in /backup/ location.

d. Please make sure script won't ask for password while copying the archive file. Additionally, the respective server user (for example, tony in case of App Server 1) must be able to run it.

e. Do not use sudo inside the script.

Note:
The zip package must be installed on given App Server before executing the script. This package is essential for creating the zip archive of the website files. Install it manually outside the script.


Task Summary

Server: App Server 3 (Stratos Datacenter)
Script Name: /scripts/ecommerce_backup.sh

Script Objectives:

a. Create a zip archive named xfusioncorp_beta.zip of /var/www/html/ecommerce.
b. Save the archive in /backup/.
c. Copy the archive to the Nautilus Backup Server in /backup/.
d. Ensure passwordless SSH access between servers.
e. Do not use sudo inside the script.

Commands used:
sudo yum update
sudo yum install zip
cd /scripts
vi ecommerce_backup.sh

zip -r /backup/xfusioncorp_ecommerce.zip /var/www/html/ecommerce
scp /backup/xfusioncorp_ecommerce.zip clint@stbkp01:/backup/

chmod 755 ecommerce_backup.sh
ssh-keygen -t rsa

ssh-copy-id clint@stbkp01
