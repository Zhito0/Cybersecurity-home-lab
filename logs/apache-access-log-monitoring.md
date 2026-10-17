Exercise 3: Apache Access Log Monitoring

Objective

Observe HTTP requests recorded by Apache on my Ubuntu virtual machine.

Lab Environment

* Client: Kali Linux (192.168.56.3)
* Web server: Ubuntu (192.168.56.2)
* Service: Apache2

Monitoring Command

sudo tail -f /var/log/apache2/access.log

Test Request

From Kali Linux, I sent an HTTP request using:

curl -I http://192.168.56.2

Observations

* Did a new log entry appear? [Record your result]
* Source IP address: [Record the observed address]
* HTTP method: [Record the observed method]
* HTTP status code: [Record the observed status]

What I Learned

Apache access logs provide a record of incoming HTTP requests. These records can help administrators troubleshoot web applications and investigate activity on a server.

Safety

Testing was performed against my own Ubuntu virtual machine in my controlled home lab.
