The Nautilus application development team is planning to launch a new PHP-based application, which they want to deploy on Nautilus infra in Stratos DC. The development team had a meeting with the production support team and they have shared some requirements regarding the infrastructure. Below are the requirements they shared:


a. Install nginx on app server 1 , configure it to use port 8095 and its document root should be /var/www/html.


b. Install php-fpm version 8.3 on app server 1, it must use the unix socket /var/run/php-fpm/default.sock (create the parent directories if don't exist).


c. Configure php-fpm and nginx to work together.


d. Once configured correctly, you can test the website using curl http://stapp01:8095/index.php command from jump host.

NOTE: We have copied two files, index.php and info.php, under /var/www/html as part of the PHP-based application setup. Please do not modify these files.

Solution:

Install nginx

yum update -y && yum install nginx -y

Configure nginx to listen on port 8095 and use /var/www/html

Edit the default nginx configuration:

sudo vi /etc/nginx/nginx.conf

Locate the server block and update it as follows:

server {
    listen       8095;
    server_name  stapp01;

    root   /var/www/html;
    index  index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include        fastcgi_params;
        fastcgi_pass   unix:/var/run/php-fpm/default.sock;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}

Explanation

listen 8095; → Nginx listens on required port

root /var/www/html; → Document root as requested

fastcgi_pass unix:/var/run/php-fpm/default.sock; → Connects nginx to PHP-FPM via Unix socket

SCRIPT_FILENAME → Ensures PHP files are executed correctly

To install PHP-FPM version 8.3 on CentOS 9 Stream, you need to enable the EPEL and Remi repositories, then use the dnf package manager to install the specific PHP module stream. 

Step 1: Enable the CRB and EPEL repositories 

The CodeReady Linux Builder (CRB) repository is required for some dependencies, and the Enterprise Linux (EPEL) repository provides additional packages. 
bash

  sudo dnf config-manager --set-enabled crb
  
  sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm -y
  
Step 2: Install and enable the Remi repository 

The Remi repository offers the latest PHP versions not available in the default CentOS streams. 


  sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm -y

Step 3: Reset the default PHP module and enable PHP 8.3 

By default, CentOS 9 might have an older PHP stream enabled. You need to reset it and enable the Remi PHP 8.3 stream. 

  sudo dnf module reset php
  
  sudo dnf module enable php:remi-8.3
  
Step 4: Install PHP 8.3 FPM and common extensions 

Now you can install PHP 8.3 along with the php-fpm package and other common extensions. 

  sudo dnf install php-fpm php-cli php-common php-mbstring php-xml -y

Step 5: Start and enable the PHP-FPM service 

After installation, start the PHP-FPM service and enable it to run automatically on boot. 

  sudo systemctl start php-fpm

  sudo systemctl enable php-fpm

Step 6: Verify the installation

Check the installed PHP version to confirm that PHP 8.3 is active. 

  php -v


Configure PHP-FPM to Use Required Unix Socket

Update PHP-FPM pool configuration

sudo vi /etc/php-fpm.d/www.conf

Make the following changes:

  listen = /var/run/php-fpm/default.sock

Start PHP-FPM

  systemctl start php-fpm

Start Nginx

  systemctl start nginx

