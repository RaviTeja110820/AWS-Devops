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

# What is DNS?
- **DNS (Domain Name System)** is like the **phonebook of the internet**.
- It translates **domain names** (e.g., `pravinmishra.in`) into **IP addresses** (e.g., `192.65.78.20`).
- Without DNS, users would need to remember IP addresses for websites.

## How DNS Works
- **Root Servers** → Direct queries to the correct TLD servers (.com, .org, .in, etc.).
- **TLD Servers** → Provide the location of the authoritative DNS server for the domain.
- **Authoritative DNS Servers** → Store the actual DNS records (A, AAAA, CNAME, MX, etc.) and return the IP.

## DNS Resolution Process (Example: devcan.in)
1. **User enters website** → e.g., `devcan.in`
2. **Check cache** → Browser, OS, or ISP may already know the IP.
3. **Ask DNS Resolver** → Resolver starts the lookup process.
4. **Go to Root Server** → Finds where the Top-Level Domain (TLD) server is.
5. **Go to TLD Server** → Example: `.in` TLD server provides info about authoritative server.
6. **Get IP Address** → Authoritative DNS server responds with the IP.
7. **Connect to Website** → Browser connects to the server using the IP.

---

## Why DNS is Important in DevOps
- **Load Balancing** → DNS can distribute traffic across multiple servers.
- **High Availability** → DNS failover directs users to healthy servers during outages.
- **Service Discovery** → In microservices, DNS helps locate services dynamically.
- **Automation** → Tools like Kubernetes, Terraform, and Ansible configure DNS records for deployments.

---
   
