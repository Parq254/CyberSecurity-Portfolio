# Cybersecurity Incident Report: Analyze Network Layer Communication

## Scenario
You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website www.yummyrecipesforme.com, and saw the error “destination port unreachable” after waiting for the page to load. 

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage  The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

![UDP packets](./ip.jpg)

In the tcpdump log, you find the following information:

1. The first two lines of the log file show the initial outgoing request from your computer to the DNS server requesting the IP address of yummyrecipesforme.com. This request is sent in a UDP packet.

2. The third and fourth lines of the log show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.

3. In front of each request and response, you find timestamps that indicate when the incident happened. In the log, this is the first sequence of numbers displayed: 13:24:32.192571. This means the time is 1:24 p.m., 32.192571 seconds.

4. After the timestamps, you will find the source and destination IP addresses. In the first line, where the UDP packet travels from your browser to the DNS server, this information is displayed as: 192.51.100.15 > 203.0.113.2.domain. The IP address to the left of the greater than (>) symbol is the source address, which in this example is your computer’s IP address. The IP address to the right of the greater than (>) symbol is the destination IP address. In this case, it is the IP address for the DNS server: 203.0.113.2.domain. For the ICMP error response, the source address is 203.0.113.2 and the destination is your computers IP address 192.51.100.15.

5. After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The plus sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. The third line displays the protocol of the response message to the browser: "ICMP," which is followed by an ICMP error message.

6. The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.

7. The remaining lines in the log indicate that ICMP packets were sent two more times, but the same delivery error was received both times. 

Now that you have captured data packets using a network analyzer tool, it is your job to identify which network protocol and service were impacted by this incident. Then, you will need to write a follow-up report. 

As an analyst, you can inspect network traffic and network data to determine what is causing network-related issues during cybersecurity incidents. Later in this course, you will demonstrate how to manage and resolve incidents. For now, you only need to analyze the situation. 

# Summary of the Problem Found in the tcpdump Log
* ### Protocols Used:*
  * UDP (User Datagram Protocol) was used for the DNS query.
  * ICMP (Internet Control Message Protocol) was used for the error response.

* ### Log Details:*
  * The log shows that the user's computer (192.51.100.15) sent UDP packets to the DNS server (203.0.113.2) on port 53, requesting the IP address for www.yummyrecipesforme.com.
  * The DNS server responded with ICMP "destination port unreachable" errors.
  * The specific error message was "udp port 53 unreachable."
  * The error was repeated multiple times.
  * The time the errors started to occur was 13:24:32.192571 which is 1:24pm 32.192571 seconds.

* ### Interpretation:*
  * The DNS server was not responding to UDP requests on port 53.
  * This indicates a problem with the DNS service on the server, potentially due to a service outage, firewall blocking, or misconfiguration.
  * The root cause of the webpage not loading is the inability to resolve the domain name to an IP address.

## Analysis and Solution
* ### Problem Report Time:* 
The issue was first observed at 1:24 p.m., 32.192571 seconds, based on the tcpdump log timestamps.

* ### Scenario, Events, and Symptoms:*
  * Customers reported being unable to access www.yummyrecipesforme.com.
  * Users received a "destination port unreachable" error in their browsers.
  * Network analysis revealed that DNS queries were failing with ICMP "udp port 53 unreachable" errors.

* ### Current Status:*
  * The website is inaccessible due to DNS resolution failures.
  * The DNS server at 203.0.113.2 is not responding to UDP requests on port 53.

* ### Information Discovered:*
  * The issue is isolated to DNS resolution.
  * ICMP errors indicate a problem with the DNS service on the server.
  * The issue is with UDP port 53, the port that the DNS service utilizes.

* ### Next Steps:*
  * Verify the status of the DNS service on the server (203.0.113.2).
  * Check the server's firewall configuration for any blocks on UDP port 53.
  * Examine the DNS server's logs for error messages.
  * Test DNS resolution from other locations to isolate the problem.
  * Restart the DNS service.
  * If restarting the service does not work, check the DNS server configuration files for errors.

* ### Suspected Root Cause:*
  * The most likely root cause is a problem with the DNS service on the server, such as a service outage, firewall blocking UDP port 53, or a misconfiguration of the DNS service.


# Cybersecurity Incidence Report
* ## Part 1: Incident Summary*

* Incident Description: Customers reported website inaccessibility (www.yummyrecipesforme.com) with "destination port unreachable" errors. Network analysis using tcpdump revealed ICMP "udp port 53 unreachable" errors from the DNS server (203.0.113.2) in response to UDP DNS queries.
* Affected Systems/Services: DNS service on server 203.0.113.2, www.yummyrecipesforme.com website.
* Date/Time of Incident: First observed at 1:24 p.m., 32.192571 seconds.
* Summary of tcpdump Log Analysis: The tcpdump log showed UDP DNS queries to port 53 of the DNS server, which were met with repeated ICMP "udp port 53 unreachable" errors. This indicates a problem with the DNS service's ability to receive UDP packets on port 53.

* ## Part 2: Incident Analysis and Resolution*

* Initial Report Details: Customers reported website inaccessibility with "destination port unreachable" errors.
* Current Status: The website is inaccessible due to DNS resolution failures. The DNS server is not responding to UDP requests on port 53.
Investigative Steps Taken: Network traffic was captured using tcpdump. The log was analyzed to identify the protocols and error messages involved.
* Information Discovered:
  * DNS queries were failing.
  * ICMP errors indicated a problem with UDP port 53 on the DNS server.
  * The domain name for the webpage could not be resolved to an IP address.
* Next Steps:
  * Verify the DNS service status.
  * Check the firewall configuration.
  * Examine DNS server logs.
  * Test DNS resolution from other locations.
  * Restart the DNS service.
  * Verify the DNS configuration files.
* Suspected Root Cause: A problem with the DNS service on the server, potentially a service outage, firewall blocking UDP port 53, or a misconfiguration.