Exercise 7: Linux Security Auditing and Attack Surface Review

Objective

Inspect listening network services on Ubuntu and compare them with a scan performed from Kali Linux.

Lab Environment

* Attacker / testing VM: Kali Linux
* Target VM: Ubuntu
* Target IP: 192.168.56.2
* Scanning tool: Nmap

Kali Linux Nmap Scan

Command:

nmap -sV 192.168.56.2

Results

* Target host was up.
* 80/tcp was open.
* Nmap identified the service as Apache HTTP Server 2.4.66 (Ubuntu).
* 999 TCP ports were reported as filtered (no response).

Ubuntu Listening-Service Inspection

Command:

sudo ss -lntup

The output showed Apache listening on port 80. Other visible listeners included local DNS resolver addresses and local CUPS printing-service ports.

Security Analysis

* The open HTTP port matches the expected Apache web server.
* The filtered ports did not respond to the Nmap scan. Filtering may explain this, but the scan alone cannot confirm the exact cause.
* Listening services should be reviewed to ensure they are needed.
* Firewall rules should allow only the connections required for the lab.

Conclusion

The scan confirmed that Ubuntu was reachable from Kali and that its HTTP service was accessible. Comparing Nmap results with Ubuntu’s listening sockets helped me understand the difference between a service listening locally and a port being reachable over the network.

Evidence

* Kali Nmap service-scan screenshot
* Ubuntu ss -lntup screenshot

Lessons Learned

* Nmap can identify reachable ports and attempt service-version detection.
* ss -lntup lists listening TCP and UDP sockets on Linux.
* Firewall filtering can affect what a remote scan reveals.
* Security auditing involves comparing local configuration with observed network exposure.
