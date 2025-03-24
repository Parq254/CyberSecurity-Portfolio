# Cybersecurity Incident Report: OS Hardening
### Scenario
You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A disgruntled baker has decided to publish the website’s best-selling recipes for the public to access for free.  The baker executed a brute force attack to gain access to the web host. 

They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After running the downloaded file, the customers are redirected to a fake version of the website where the seller’s recipes are now available for free. Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. 

They complained that the company’s website had prompted them to download a file to update their browsers. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly.  In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event. To address the incident, you create a sandbox environment to observe the suspicious website behavior. 

You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. As soon as the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which is designed to look like the original site. However, the recipes your company sells are now posted for free on the new website. 
The logs show the following process:

1. The browser requests a DNS resolution of the yummyrecipesforme.com URL
2. The DNS replies with the correct IP address
3. The browser initiates an HTTP request for the webpage
4. The browser initiates the download of the malware
5. The browser requests another DNS resolution for greatrecipesforme.com
6. The DNS server responds with the new IP address
7. The browser initiates an HTTP request to the new IP address

A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com.  The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled baker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack.  Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website.  You should also recommend a security action to take to prevent brute force attacks in the future.

# Reading DNS & HTTP Traffic log

| Feature | DNS Traffic Logs | HTTP Traffic Logs | Interpretation/Use |
| :--- | :--- | :--- | :--- |
| **Timestamp** | Time of DNS query/response. | Time of HTTP request/response. | Chronological ordering of events, time-based correlation. |
| **Source IP/Port** | IP address and port of the querying device. | IP address and port of the client making the request. | Identifying the origin of network traffic. |
| **Destination IP/Port** | IP address and port of the DNS server. | IP address and port of the web server. | Identifying the destination of network traffic. Port 53 is common for DNS, 80 for HTTP, 443 for HTTPS. |
| **Domain Name** | Domain name being queried (e.g., example.com). | Hostname in the HTTP request (e.g., example.com). | Seeing which domain names are being resolved. Potential for detecting malicious domains. |
| **Query Type** | A (address), AAAA (IPv6 address), CNAME (canonical name), MX (mail exchange), etc. | HTTP request method (GET, POST, PUT, DELETE, etc.). | Understanding the type of DNS lookup or HTTP action. |
| **Response Code** | DNS response codes (e.g., NOERROR, NXDOMAIN). | HTTP status codes (e.g., 200 OK, 404 Not Found, 500 Internal Server Error). | Indicating the success or failure of the DNS query or HTTP request. |
| **Requested resource** | N/A | URL requested (e.g. /index.html, /api/data) | seeing what resources are being requested from the webserver. |
| **User-Agent** | N/A | User-Agent string. | Shows the type of browser or application making the http request. Can be used to find unusual or malicious user agents. |
| **Referer** | N/A | Referer Header | shows what webpage that the user was on, before they made the current webpage request. |
| **Content-Length** | N/A | Content-Length Header | shows the size of the data being sent in the http response. |
| **DNS Records** | Resolved IP addresses, CNAME records, etc. | N/A | The actual data returned from the DNS server. |
| **Flags** | DNS flags. | TCP Flags inside of the HTTP traffic. | Flags give extra information about the packet. For example, TCP flags like SYN, ACK, FIN, RST. |
| **Payload Data** | N/A | Data sent in HTTP requests (e.g., form data) or responses (e.g., HTML content). | Reveals the content of the HTTP communication. |

### Trffic Log

| Traffic Log Type | Description | Uses |
| :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Network Traffic Logs** | Detailed record of network packet data, including source and destination IP addresses and ports, protocols (TCP, UDP, ICMP), timestamps, packet flags, and payload information (if captured). | Network troubleshooting, security monitoring (detecting suspicious activity), incident response (investigating attacks), performance analysis (latency, packet loss), and forensic analysis (reconstructing network events). |
| **Web Server Access Logs** | Records of HTTP requests received by a web server, including client IP addresses, request timestamps, requested URLs, HTTP status codes, user-agent strings, referer headers, and content lengths. | Website traffic analysis (tracking user behavior), performance monitoring (identifying slow-loading pages), security auditing (detecting unauthorized access), and analyzing application usage patterns. |
| **Firewall Logs** | Records of allowed and blocked network traffic, containing source and destination IP addresses and ports, protocols, firewall rule actions (allow or deny), and timestamps. | Security monitoring (detecting unauthorized access attempts), incident response (identifying blocked attacks), and network access control auditing. |
| **DNS Logs** | Records of DNS queries and responses, including domain names, resolved IP addresses, DNS record types (A, AAAA, CNAME), and DNS server information. | Detecting malicious domain usage (phishing, malware distribution), troubleshooting DNS resolution issues, and analyzing network domain resolution patterns. |
| **IDS/IPS Logs** | Records of detected security threats and intrusion attempts, including attack signatures, source and destination IP addresses, attack timestamps, and actions taken by the intrusion detection/prevention system. | Security monitoring (identifying intrusion attempts), incident response (blocking attacks and analyzing their impact), and generating security alerts. |

# Response
## Incident Documentation

### Incident Summary:
* A former employee conducted a brute force attack to gain unauthorized access to the yummyrecipesforme.com web server's admin panel.
* Malicious JavaScript code was injected into the website's source code, prompting users to download malware.
* Downloaded malware redirected users to a fake website, greatrecipesforme.com.
* The admin password was changed.

### Affected Systems:
* yummyrecipesforme.com web server.
* User computers that downloaded and executed the malware.

### Timeline:
* Brute force attack and unauthorized access.
* Injection of malicious JavaScript.
* Malware distribution and redirection.
* Customer reports of suspicious activity.
* Website owner unable to log in.

### Technical Details:
* Brute force attack exploiting default admin password.
* JavaScript injection to trigger malware download.
* Malware redirection to greatrecipesforme.com.
* Network protocols involved: DNS, HTTP.

### Indicators of Compromise (IOCs):
* Modified website source code.
* Malicious executable file download.
* Redirection to greatrecipesforme.com.
* Unusual admin login attempts.

# Recommended Security Action

To prevent future brute force attacks, I recommend implementing the following security measures:

* ### Account Lockout Policy:*
  * Implement an account lockout policy that temporarily disables an account after a specified number of failed login attempts.
  * This will prevent attackers from repeatedly trying passwords.

* ### Strong Password Policy:*
  * Enforce a strong password policy that requires users to create complex passwords with a combination of uppercase and lowercase letters, numbers, and symbols.
  * Regularly require password changes.

* ### Multi-Factor Authentication (MFA):*
  * Implement MFA for administrative accounts.
  * MFA requires users to provide a second form of authentication (e.g., a code from a mobile app) in addition to their password.

* ### Intrusion Detection/Prevention System (IDS/IPS):*
  * Implement an IDS/IPS that is configured to detect and block brute force attacks.

* ### Web Application Firewall (WAF):*
  * A WAF can help to block malicious requests, and can be configured to block unusual amounts of login attempts.

* ### Rate Limiting:*
  * Implement rate limiting on login attempts, so that a large number of login attempts from one ip address will be blocked.

* ### Regular Security Audits:*
  * Perform regular security audits to identify and address potential vulnerabilities.

* ### Principle of Least Privilege:*
Ensure that admin accounts have only the privileges they need, and no more.

* ### Change Default Credentials:*
Ensure that all default credentials are changed immediately after any installation.
