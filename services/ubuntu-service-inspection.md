Exercise 4: Ubuntu Service Inspection

Objective

Inspect running services on Ubuntu and verify the installed Apache HTTP Server version.

Lab Environment

* Target: Ubuntu Linux
* IP address: 192.168.56.2
* Web server: Apache2
* Testing machine: Kali Linux

Commands Used

Check Apache status

systemctl is-active apache2
systemctl status apache2 --no-pager

Verify Apache version

apache2 -v
dpkg-query -W -f='${Package} ${Version}\n' apache2

List running services

systemctl list-units --type=service --state=running --no-pager

Inspect listening ports

sudo ss -lntup

Results

* Apache service status: [Record your result]
* Apache server version: [Record your result]
* Installed package version: [Record your result]
* Listening address and port for Apache: [Record your result]
* Other observations: [Record relevant findings]

Analysis

The purpose of this exercise is to identify active services, verify the installed web server version, and determine which network addresses and ports are listening.

These findings provide a baseline for future security hardening and comparison with network scans performed from Kali Linux.

What I Learned

* How to inspect services using systemd.
* How to verify installed software versions.
* How to identify listening TCP and UDP ports.
* Why service inventory is an important part of system security.

Safety

All inspection was performed on my own Ubuntu virtual machine in my controlled home lab.
