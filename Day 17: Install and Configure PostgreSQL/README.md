The Nautilus application development team has shared that they are planning to deploy one newly developed application on Nautilus infra in Stratos DC. The 
application uses PostgreSQL database, so as a pre-requisite we need to set up PostgreSQL database server as per requirements shared below:

PostgreSQL database server is already installed on the Nautilus database server.

a. Create a database user kodekloud_sam and set its password to dCV3szSGNA.

b. Create a database kodekloud_db4 and grant full permissions to user kodekloud_sam on this database.

Note: Please do not try to restart PostgreSQL server service.


Solution:

1. Log in to PostgreSQL

  sudo -u postgres psql

2. Create a New User

  CREATE USER kodekloud_db4 WITH ENCRYPTED PASSWORD 'dCV3szSGNA';

3. Create a New Database
   
  CREATE DATABASE kodekloud_db4;
  
4. Grant Permissions to the User

  GRANT ALL PRIVILEGES ON DATABASE kodekloud_db4 TO kodekloud_sam;

5. Exit psql
   \q

6. Verify the setup

   psql -d kodekloud_db4 -U kodekloud_sam -h localhost
