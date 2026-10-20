Ubuntu Authentication Log Review

Objective

Review Ubuntu authentication and system logs to understand routine administrative activity and investigate potential failed-login events.

Lab Environment

* Operating system: Ubuntu Linux
* Testing machine: Kali Linux
* Log sources: /var/log/auth.log, where available, and the systemd journal
* Investigation tools: journalctl, grep, and systemctl

1. Initial Log Review

I inspected the authentication log using:

sudo tail -n 30 /var/log/auth.log

The output included sudo/PAM messages showing that a session was opened for root by my Ubuntu VM user while privileged commands were executed.

I also inspected recent system journal entries:

sudo journalctl -b --no-pager -n 30

Some service-related and DNS-related messages were present. These messages require further context before their significance can be determined.

2. Search for Failed Authentication

I searched the current boot’s journal for common authentication-related messages:

sudo journalctl -b --no-pager | grep -Ei 'Failed password|authentication failure|FAILED LOGIN|invalid user'

Observed result: No matching lines were returned.

This means the search did not find messages matching those patterns in the current boot’s journal. It does not prove that no failed authentication attempts have ever occurred.

3. SSH Service Assessment

I checked the SSH service:

systemctl is-active ssh

Observed result: inactive

I checked whether the OpenSSH server package was installed:

dpkg-query -W -f='${Status}\n' openssh-server

Observed result: The package was reported as not installed.

SSH was not installed solely for this exercise because direct VirtualBox console access was sufficient for the current lab.

4. Controlled Local Authentication Test

I attempted to switch to a deliberately nonexistent local account:

su - labuser_does_not_exist

Ubuntu reported that the specified user did not exist or that the user entry was incomplete.

I then searched the current boot’s journal:

sudo journalctl -b --no-pager | grep -Ei 'labuser_does_not_exist|authentication failure|FAILED SU'

Observed result: No matching lines were returned.

This indicates only that the search did not find matching journal messages. Logging behavior can vary depending on the authentication mechanism and system configuration.

5. Findings and Conclusion

* The logs included routine sudo/PAM administrative activity.
* The initial failed-authentication search returned no matching lines.
* The SSH service was inactive, and the OpenSSH server package was not installed.
* The controlled nonexistent-user test was rejected by Ubuntu.
* The follow-up journal search returned no matching lines.
* No confirmed security incident was identified during this exercise.

6. Skills Practiced

* Inspecting Linux authentication logs.
* Filtering system journal entries with grep.
* Checking service status and package installation.
* Performing a controlled local authentication test.
* Recording observations without assuming that every warning or error indicates an attack.

7. Evidence

Screenshots of the log review, SSH checks, nonexistent-user message, and search results will be added to the repository where available.
