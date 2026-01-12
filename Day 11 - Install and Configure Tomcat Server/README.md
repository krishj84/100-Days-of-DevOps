The Nautilus application development team recently finished the beta version of one of their Java-based applications, which they are planning to deploy on one of the app servers in Stratos DC. After an internal team meeting, they have decided to use the tomcat application server. Based on the requirements mentioned below complete the task:


a. Install tomcat server on App Server 2.

b. Configure it to run on port 5002.

c. There is a ROOT.war file on Jump host at location /tmp.


Deploy it on this tomcat server and make sure the webpage works directly on base URL i.e curl http://stapp02:5002


Command:

yum update -y && yum update tomcat

Copy the war file from jumphost

scp /tmp/ROOT.war steve@stapp02:/etc/shared/tomcat/webapps

Change the port from 8080 to 5002 in server.xml

Start the tomcat service

systemctl start tomcat

Test the application using curl from jumphost

curl http://stapp02:5002
