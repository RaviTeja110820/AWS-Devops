# AWS-Devops
# Rule of Data Transfer: Protocols

## Internet Protocol (IP)
- Defines how data packets are addressed and routed between systems.
- Provides unique identifiers for machines in a network (IP addresses).
- Two versions:
  - **IPv4** → Example: `192.65.78.20`
  - **IPv6** → Example: `2001:0db8:85a3::8a2e:0370:7334`

## Transmission Control Protocol (TCP)
- Works with IP (TCP/IP stack).
- Reliable: ensures **acknowledgment, retransmission, and ordered delivery**.
- Commonly used by:
  - **SSH** (remote login)  
  - **FTP** (file transfer)  
  - **HTTP/HTTPS** (web traffic)

## User Datagram Protocol (UDP)
- Faster but unreliable (no acknowledgments).
- Useful for real-time communication where speed matters more than reliability.
- Examples:
  - **Video/voice calls** (Zoom, Skype)  
  - **Online gaming**  
  - **Streaming services** (live events)

## HTTP and HTTPS
- **HTTP**: Protocol for transferring hypertext and resources on the web.
- **HTTPS**: Secure version with **SSL/TLS encryption**.
- Widely used in web applications, REST APIs, and microservices.

## Other Important Protocols
- **SSH (Secure Shell):** Secure remote login to servers (commonly used in cloud/DevOps).  
- **DNS (Domain Name System):** Resolves domain names (e.g., `google.com`) into IP addresses.  
- **SMTP/IMAP/POP3:** Email communication protocols.  
- **SNMP:** Monitoring and managing devices in a network.  
- **NTP (Network Time Protocol):** Keeps servers in sync with accurate time (important in logging and distributed systems).

## Summary
- **TCP/IP** → Foundation of internet and cloud communication.  
- **UDP** → Best for real-time services.  
- **HTTP/HTTPS** → Backbone of web and APIs (important in CI/CD pipelines, APIs, microservices).  
- **SSH** → Critical for server access, automation scripts, and deployments.  
- **DNS & NTP** → Essential for service reliability and synchronization.  


   
