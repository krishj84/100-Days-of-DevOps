There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.

Look into the issue and fix the same.

Commnads:
To check the status of MariaDB servive
systemctl status mariadb

Issue:
Jan 10 17:41:45 stdb01.stratos.xfusioncorp.com mariadbd[2351]: 2026-01-10 17:41:45 0 [Warning] Can't create test file '/var/lib/mysql/stdb01.lower-test' (Errcode: 13 "Permission denied")

drwxr-xr-x 1 root mysql 4096 Jan 10 17:39 mysql
[root@stdb01 lib]# chown mysql:mysql mysql

systemctl restart mariadb


