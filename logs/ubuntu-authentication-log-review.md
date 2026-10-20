SSH Service Assessment

Commands used:

systemctl is-active ssh
dpkg-query -W -f='${Status}\n' openssh-server

Findings:

* The SSH service returned inactive.
* The OpenSSH server package was reported as not installed.
* SSH was not installed solely for this exercise because direct VM console access is sufficient for the current lab.

Security relevance:

Not installing an unnecessary network service helps minimize the system’s exposed attack surface.

Controlled Authentication Test

A local authentication test using the deliberately nonexistent username labuser_does_not_exist was attempted.

Log search result: To be completed after checking the system journal.

This test is intended to demonstrate how local authentication failures may be logged. It does not, by itself, demonstrate a successful attack or a security incident.
