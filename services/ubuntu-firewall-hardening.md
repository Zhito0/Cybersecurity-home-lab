Ubuntu Firewall Hardening with UFW

Objective

Configure the Ubuntu firewall using Uncomplicated Firewall (UFW), restrict incoming connections by default, and verify that the Apache web server remains accessible from Kali Linux.

Lab Environment

* Server: Ubuntu Linux
* Testing machine: Kali Linux
* Ubuntu IP address: 192.168.56.2
* Kali IP address: 192.168.56.3
* Web server: Apache2
* Firewall tool: UFW

1. Initial Firewall Assessment

I checked the firewall status before making changes:

sudo ufw status verbose

The initial result was:

Status: inactive

This confirmed that UFW was not active before the hardening exercise.

2. Firewall Configuration

I added a rule allowing HTTP traffic from the lab’s host-only subnet:

sudo ufw allow from 192.168.56.0/24 to any port 80 proto tcp

This rule allows TCP connections to port 80 from the specified lab subnet.

I reviewed the firewall rules:

sudo ufw status numbered

I configured the default incoming policy to deny unsolicited incoming connections:

sudo ufw default deny incoming

I configured the default outgoing policy to allow outgoing connections:

sudo ufw default allow outgoing

I then enabled the firewall:

sudo ufw enable

3. Firewall Verification

I checked the firewall status after enabling it:

sudo ufw status verbose

Result: The firewall configuration was applied. The final status and listed rules should be confirmed against the command output.

The intended configuration is:

* UFW is active.
* Incoming connections are denied by default.
* Outgoing connections are allowed by default.
* HTTP traffic from 192.168.56.0/24 is allowed to TCP port 80.

4. Apache Service Verification

I checked that Apache remained active:

systemctl is-active apache2

Observed result: active

5. HTTP Connectivity Test from Kali Linux

From Kali Linux, I ran:

curl -I http://192.168.56.2

The server returned:

HTTP/1.1 200 OK

The response headers also identified Apache as the web server.

This confirmed that Kali could still reach the Ubuntu web server over HTTP after the firewall configuration.

6. Learning Outcomes

* Learned how to inspect the initial UFW status.
* Practiced configuring a firewall rule for a specific subnet and service.
* Set default incoming and outgoing firewall policies.
* Enabled UFW and checked its status.
* Verified that Apache remained active.
* Tested HTTP connectivity from Kali Linux after hardening.

7. Security Considerations

The firewall limits incoming connections according to the configured rules. Allowing HTTP from the lab subnet keeps the test web server accessible to the Kali VM.

This is a basic lab hardening exercise, not a complete security assessment. Additional work could include reviewing exposed services, applying system updates, reviewing logs, and checking Apache security settings.

8. Evidence

Screenshots to include:

* Initial UFW status showing inactive.
* The firewall configuration commands.
* Final UFW status showing active and the configured rules.
* Apache service status showing active.
* Kali HTTP test returning HTTP/1.1 200 OK.
