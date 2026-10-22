Exercise 10: OWASP Juice Shop Deployment

Objective

Deploy OWASP Juice Shop on Ubuntu using Docker and verify that it is accessible from Kali Linux over the home lab network.

Lab Environment

* Host machine: MacBook
* Virtualization: VirtualBox
* Target VM: Ubuntu Linux
* Testing VM: Kali Linux
* Ubuntu host-only IP: 192.168.56.2
* Application port: 3000

Setup

Installed Docker on Ubuntu and downloaded the OWASP Juice Shop image.

Image:

bkimminich/juice-shop

Started the container with a host-only IP binding:

sudo docker run -d --name juice-shop --restart unless-stopped -p 192.168.56.2:3000:3000 bkimminich/juice-shop

Verification

Checked the container status:

sudo docker ps

Result: The juice-shop container was running, with port 3000 mapped to 192.168.56.2.

Tested HTTP connectivity from Kali:

curl -I http://192.168.56.2:3000

Result: Received an HTTP response.

Opened the application in Firefox on Kali:

http://192.168.56.2:3000

Result: The OWASP Juice Shop web interface loaded successfully.

Security Considerations

* Juice Shop is intentionally vulnerable and is used only for authorized training.
* The container port is bound to the Ubuntu host-only IP rather than all host interfaces.
* The lab should remain isolated from untrusted networks.
* No vulnerability exploitation was performed in this exercise.

Conclusion

Successfully deployed OWASP Juice Shop using Docker and verified access from Kali Linux. The lab is ready for controlled web application security exercises.

Evidence

* Screenshot of sudo docker ps
* Screenshot of the Juice Shop interface in Kali Firefox
* Screenshot of the successful HTTP connectivity test
