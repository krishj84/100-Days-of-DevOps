Day by day traffic is increasing on one of the websites managed by the Nautilus production support team. Therefore, the team has observed a degradation in website performance. Following discussions about this issue, the team has decided to deploy this application on a high availability stack i.e on Nautilus infra in Stratos DC. They started the migration last month and it is almost done, as only the LBR server configuration is pending. Configure LBR server as per the information given below:


a. Install nginx on LBR (load balancer) server.

b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf.

c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers.

d. Once done, you can access the website using StaticApp button on the top bar.

Solution:

yum update -y && yum install nginx -y

1. Define the Upstream Group
   
   http {
   
    # ... other http settings ...

    upstream backend_servers {
   
        server 192.168.1.101:8080; # App server 1
   
        server 192.168.1.102:8080; # App server 2
   
        server 192.168.1.103:8080; # App server 3
   
    }

3. Configure a Server Block to Proxy Requests
   
   location / {
   
            proxy_pass http://backend_servers; # Forward requests to the upstream group
   
   }
