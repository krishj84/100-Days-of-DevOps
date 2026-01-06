Following a security audit, the xFusionCorp Industries security team has opted to enhance application and server security with SELinux. To initiate testing, the following requirements have been established for App server 1 in the Stratos Datacenter:


Install the required SELinux packages.

Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes.

No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight.

Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled.

<img width="1242" height="551" alt="Screenshot 2026-01-05 at 6 45 36 PM" src="https://github.com/user-attachments/assets/d3e24a6b-1fcd-4584-bc07-ea44c5df8f34" />

<img width="743" height="559" alt="Screenshot 2026-01-05 at 6 49 28 PM" src="https://github.com/user-attachments/assets/4984163e-70df-4cef-9a97-7a6dbcc009b1" />

<img width="734" height="183" alt="Screenshot 2026-01-05 at 6 50 15 PM" src="https://github.com/user-attachments/assets/f075815d-8b59-404a-9d4d-f96a71091d51" />

vi config

Update SELinux to "disabled"

<img width="743" height="530" alt="Screenshot 2026-01-05 at 6 51 05 PM" src="https://github.com/user-attachments/assets/07ef5c21-aae3-4523-bb3d-e105d6f1ed75" />


