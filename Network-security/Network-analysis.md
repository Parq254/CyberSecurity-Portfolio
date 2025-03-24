# Cybersecurity Incident Report: Analyze Network Attacks

## Scenario
You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

## Attack Type
The symptoms strongly indicate a SYN flood attack.
* A SYN flood attack is a type of Denial-of-Service (DoS) attack.
* The attacker sends a large number of SYN (synchronize) requests to the target server, but never completes the TCP handshake.
* This leaves the server with numerous half-open connections, consuming its resources and preventing it from responding to legitimate requests.

# Deep Explanation of Attack
To explain how a SYN flood attack causes a website malfunction, let's break down the TCP three-way handshake and how the attack disrupts it:

### Normal TCP Three-Way Handshake:

* SYN (Synchronize): A client (e.g., a web browser) sends a SYN packet to the server, requesting a connection.
* SYN-ACK (Synchronize-Acknowledge): The server receives the SYN packet and responds with a SYN-ACK packet, acknowledging the client's request and indicating its willingness to establish a connection.
* ACK (Acknowledge): The client receives the SYN-ACK packet and sends an ACK packet back to the server, confirming the connection establishment.