Exercise 8: Linux User and Permission Auditing

Objective

Inspect Ubuntu user accounts and review permissions on important system account files.

Environment

* Operating system: Ubuntu Linux
* Current user: vboxuser
* User ID (UID): 1000

User Account Review

Command used:

whoami
id
getent passwd

The output showed the current user and multiple system/service accounts. Service accounts such as www-data, systemd-resolve, and cups are normal on Ubuntu and are commonly used to run individual services with limited privileges.

File Permission Review

Commands used:

ls -l /etc/passwd /etc/shadow /etc/group
stat -c '%A %a %U:%G %n' /etc/passwd /etc/shadow /etc/group

Results

File	Permissions	Owner
/etc/passwd	644 (-rw-r--r--)	root:root
/etc/shadow	640 (-rw-r-----)	root:shadow
/etc/group	644 (-rw-r--r--)	root:root

Security Analysis

* /etc/passwd and /etc/group are readable by all users but writable only by root.
* /etc/shadow has more restrictive access because it contains sensitive password-hash information.
* The observed permissions are consistent with common Ubuntu defaults.
* No permissions were changed during this exercise.

Conclusion

This audit helped me understand Linux user accounts, service accounts, file ownership, and permission modes. I learned why sensitive account information should have stricter access controls than general account and group information.

Evidence

* Screenshot of user account information
* Screenshot of file permission inspection

Lessons Learned

* whoami identifies the current user.
* id displays user and group IDs.
* getent passwd lists accounts known to the system.
* ls -l and stat help inspect file permissions and ownership.
* Numeric permission 640 is more restrictive than 644.
