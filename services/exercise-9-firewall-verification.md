Exercise 9: Firewall Verification and Network Testing

Objective

Verify the Ubuntu firewall configuration and confirm that the intended HTTP service remains accessible from Kali Linux.

Lab Environment

* Target: Ubuntu Linux
* Testing machine: Kali Linux
* Target IP: 192.168.56.2
* Testing tool: Nmap

1. Firewall Status

Command:

sudo ufw status verbose

Observed:

* UFW status: active
* Default incoming policy: deny
* Default outgoing policy: allow
* Routed traffic: disabled
* HTTP traffic on TCP port 80 is allowed from the lab subnet.

2. HTTP Connectivity Test

Command:

curl -I http://192.168.56.2

Result: HTTP/1.1 200 OK

This confirms that Apache successfully responded to the request from Kali.

3. Nmap Service Scan

Command:

nmap -sV 192.168.56.2

Observed:

* Target host was up.
* TCP port 80 was open.
* Nmap identified the HTTP service as Apache httpd 2.4.66.

Security Analysis

The firewall is active and the intended HTTP service is reachable from the lab network. The observed result is consistent with the configured HTTP allow rule.

This scan verifies the state of the common ports tested by Nmap; it does not prove that every possible port or network path is secure.

Conclusion

I verified the Ubuntu firewall status, tested HTTP connectivity from Kali, and used Nmap to identify the reachable web service. This exercise demonstrated how firewall rules affect network access while allowing intended services to remain available.

Evidence

* Screenshot of sudo ufw status verbose
* Screenshot of the Kali curl -I result
* Screenshot of the Kali Nmap service scan
