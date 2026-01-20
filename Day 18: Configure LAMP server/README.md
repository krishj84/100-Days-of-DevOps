xFusionCorp Industries is planning to host a WordPress website on their infra in Stratos Datacenter. They have already done infrastructure configuration—for example, on the storage server they already have a shared directory /vaw/www/html that is mounted on each app host under /var/www/html directory. Please perform the following steps to accomplish the task:

a. Install httpd, php and its dependencies on all app hosts.

b. Apache should serve on port 8082 within the apps.

c. Install/Configure MariaDB server on DB Server.

d. Create a database named kodekloud_db4 and create a database user named kodekloud_cap identified as password TmPcZjtRQx. Further make sure this newly created user is able to perform all operation on the database you created.

e. Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App is able to connect to the database using user kodekloud_cap

Solution:

On all the AppServers

  Install httpd/php/mysql

    yum update -y && yum install httpd php php-mysqlnd php-fpm -y

  Update the port # in /etc/httpd/cpnf/http.conf

  systemctl start httpd

On the DB server

Install mariadb

   yum update -y && yum install mariadb-server mariadb -y

Start the mariadb service:

  systemctl start mariadb

Secure the MariaDB Installation:

Run the built-in security script to set the root password and remove insecure defaults: 

  mysql_secure_installation

Access the MariaDB Shell:

Log in to the MariaDB shell as the root user using the password you set in the previous step: 

  mysql -u root -p
  
Create a Database, User, and Assign Permissions:

  CREATE DATABASE kodekloud_db4;

  CREATE USER 'kodekloud_cap'@'%' IDENTIFIED BY 'TmPcZjtRQx';

  GRANT ALL PRIVILEGES ON kodekloud_db4.* TO 'kodekloud_cap'@'%';

Apply the changes:

  FLUSH PRIVILEGES;


