Apache ServerName Configuration

Objective

Resolve the Apache warning about an unspecified fully qualified domain name and verify that the web server configuration remains valid.

Lab Environment

* Web server: Apache2
* Operating system: Ubuntu
* Ubuntu lab IP: 192.168.56.2
* Testing machine: Kali Linux
* Web server URL: http://192.168.56.2

Initial Finding

While checking the Apache configuration, I ran:

sudo apache2ctl configtest

Apache displayed a warning that it could not reliably determine the server’s fully qualified domain name and recommended setting the global ServerName directive.

The command also returned:

Syntax OK

This indicated that the configuration syntax was valid despite the warning.

Remediation

I configured Apache to use the Ubuntu VM’s host-only IP address as its server name:

echo "ServerName 192.168.56.2" | sudo tee /etc/apache2/conf-available/servername.conf

I then enabled the configuration:

sudo a2enconf servername

Validation

I checked the Apache configuration again:

sudo apache2ctl configtest

Expected result:

Syntax OK

After confirming the configuration was valid, I reloaded Apache:

sudo systemctl reload apache2

Finally, I checked the service status:

systemctl is-active apache2

Expected result:

active

Learning Outcomes

* Learned how to interpret an Apache configuration warning.
* Practiced creating and enabling an Apache configuration file.
* Used apache2ctl configtest to validate configuration syntax.
* Used systemctl to reload and verify a Linux service.

Security Note

Setting ServerName resolves the naming warning but does not, by itself, harden Apache security. Additional security measures will be assessed separately.

Evidence

Screenshots of the configuration test and service verification will be added after confirming the final results.
