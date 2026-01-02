Question:
Create a user named kirsty on App Server 3 in Stratos Datacenter. Set the expiry date to 2024-04-15, ensuring the user is created in lowercase as per standard protocol.

[banner@stapp03 ~]$ sudo useradd -m -e 2024-04-15 kirsty

-m --> Create a home directory
-e 2024-04-15 --> Sets the account expiration date (after this date, login is disabled)

[banner@stapp03 ~]$ sudo chage -l kirsty

Last password change                                    : Jan 02, 2026

Password expires                                        : never

Password inactive                                       : never

Account expires                                         : Apr 15, 2024

Minimum number of days between password change          : 0

Maximum number of days between password change          : 99999

Number of days of warning before password expires       : 7


