The production support team of xFusionCorp Industries has deployed some of the latest monitoring tools to keep an eye on every service, application, etc. running on the systems. One of the monitoring systems reported about Apache service unavailability on one of the app servers in Stratos DC.


Identify the faulty app host and fix the issue. Make sure Apache service is up and running on all app hosts. They might not have hosted any code yet on these servers, so you don’t need to worry if Apache isn’t serving any pages. Just make sure the service is up and running. Also, make sure Apache is running on port 5000 on all app servers.


Solution:

Test the connectivity to each of the appserver

  curl http://stapp01:5000  - Not Working

  curl http://stapp02:5000 - Working

  curl http://stapp03:5000 - Working

On AppServer1 5000 port is used by sendmail application

  netstat -tulnp | grep -i 5000

Changed the port of sendmail to 25 and restart the sendmail service (/etc/mail/sendmail.cf)

  systemctl restart sendmail

Restart httpd process

  systemctl restart httpd

Now test the connectivity

  curl http://stapp01:5000  - Working

