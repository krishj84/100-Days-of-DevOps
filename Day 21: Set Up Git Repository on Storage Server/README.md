The Nautilus development team has provided requirements to the DevOps team for a new application development project, specifically requesting the establishment of a Git repository. Follow the instructions below to create the Git repository on the Storage server in the Stratos DC:

Utilize yum to install the git package on the Storage Server.

Create a bare repository named /opt/demo.git (ensure exact name usage).


Solution:

Install GIT

  yum update -y && yum install git

  git --version

Create a base repository

  cd /opt

  mkdir demo.git

  cd demo.git

  git inint --bare

bare --> A bare repository does not have a working directory (no files are checked out), only the contents of the .git folder. 
