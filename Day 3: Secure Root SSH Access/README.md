Day 3: Secure Root SSH Access

Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.

Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

Steps:

ssh tony@stapp01

Sudo su

Change the password for the root user

Try to login as root user

Update the /etc/ssh/sshd_config file

Change PermitRootLogin value from Yes to No

Restart the service

systemctl restart sshd

<img width="744" height="538" alt="Screenshot 2026-01-03 at 9 45 52 AM" src="https://github.com/user-attachments/assets/55630595-57dd-4338-a084-ced787320a9f" />

<img width="684" height="141" alt="Screenshot 2026-01-03 at 9 46 37 AM" src="https://github.com/user-attachments/assets/bc666d32-d910-48fb-b0af-ca04514d2835" />

<img width="742" height="567" alt="Screenshot 2026-01-03 at 9 48 44 AM" src="https://github.com/user-attachments/assets/5b91b38f-d3bd-4bbe-8f42-adce7ac74206" />

<img width="707" height="112" alt="Screenshot 2026-01-03 at 9 50 46 AM" src="https://github.com/user-attachments/assets/d95fd920-c9b7-42e0-ac09-e2df2d338b8d" />







