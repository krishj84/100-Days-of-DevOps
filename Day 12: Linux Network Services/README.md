Our monitoring tool has reported an issue in Stratos Datacenter. One of our app servers has an issue, as its Apache service is not reachable on port 3002 (which is the Apache port). The service itself could be down, the firewall could be at fault, or something else could be causing the issue.


Use tools like telnet, netstat, etc. to find and fix the issue. Also make sure Apache is reachable from the jump host without compromising any security settings.

Once fixed, you can test the same using command curl http://stapp01:3002 command from jump host.

Note: Please do not try to alter the existing index.html code, as it will lead to task failure.

Solution:
Check the status oh httpd process

systemctl status httpd

Error:

Jan 14 00:31:16 stapp01.stratos.xfusioncorp.com httpd[896]: (98)Address alr
eady in use: AH00072: make_sock: could not bind to address 0.0.0.0:3002
Jan 14 00:31:16 stapp01.stratos.xfusioncorp.com httpd[896]: no listening so
ckets available, shutting down

netstat -tulnp

[root@stapp01 tony]# netstat -tulnp | grep -i 3002

tcp        0      0 127.0.0.1:3002          0.0.0.0:*               LISTEN      500/sendmail: accep 


The primary configuration file for Sendmail is typically located at /etc/mail/sendmail.cf

Change the port from 3002 to 25

Port 25 (SMTP): The traditional port for Mail Transfer Agents (MTAs) to send and receive mail between servers.

systemctl restart sendmail

Restart the httpd process

systemctl restart httpd

To list IPTABLEs

iptables -L

To add an iptables rule, use sudo iptables -A

sudo iptables -A <CHAIN> -p <PROTOCOL> --dport <PORT> -j <ACTION>

<img width="1790" height="738" alt="image" src="https://github.com/user-attachments/assets/2b6cb0c6-ea0d-497d-a8d9-739ab0a0d504" />

<img width="1780" height="932" alt="image" src="https://github.com/user-attachments/assets/02c4b7a0-5e5d-400f-8d12-83261cec0fe3" />

Test the curl command now

curl http://stapp01:3002



