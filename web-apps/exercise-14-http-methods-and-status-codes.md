Exercise 14: HTTP Methods and Status Codes

Objective

Observe HTTP methods, status codes, and API responses while interacting with OWASP Juice Shop in the local cybersecurity lab.

Environment

* Target application: OWASP Juice Shop
* Target URL: http://192.168.56.2:3000
* Tool: Firefox Developer Tools — Network panel

Procedure

1. Opened OWASP Juice Shop in Firefox.
2. Opened Developer Tools and selected the Network panel.
3. Searched for APPLE and observed the resulting network requests.
4. Opened a product and inspected its network activity.
5. Selected a successful GET request and reviewed its Headers and Response tabs.

Observations

Product search

* Observed HTTP method: GET
* Observed status: 304 Not Modified

A 304 response indicates that the browser may use a previously cached response rather than downloading the resource again.

Product reviews API

* Request method: GET
* Endpoint: /rest/products/24/reviews
* Observed status: 200 OK
* Protocol: HTTP/1.1
* Response format: JSON
* Observed response: {"status":"success","data":[]}

The response indicated success, but the returned data array was empty for this request.

The selected request showed no request payload, which is normal for a typical GET request.

Additional observations

While opening a product, I observed both 200 OK and 304 Not Modified responses. The requests I inspected during these actions used the GET method.

Analysis

* GET requests are commonly used to retrieve resources or information.
* 200 OK indicates that a request was successfully processed.
* 304 Not Modified is associated with HTTP caching.
* An empty JSON array does not, by itself, indicate a security vulnerability.
* Inspecting the endpoint and response helps explain what the application is requesting and returning.

Conclusion

This exercise provided practical experience identifying HTTP methods, interpreting common status codes, and inspecting JSON responses in browser developer tools. The observations describe normal application behavior and do not, by themselves, establish a vulnerability.

Evidence

Attach a screenshot of the selected request showing the request URL and status code, and another screenshot of the JSON response. Hide any sensitive session identifiers before uploading screenshots.
