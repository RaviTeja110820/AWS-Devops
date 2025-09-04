# AWS-Devops
# 📌  Rule of Data Transfer: Protocols

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

# 📌  What is DNS?
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

## DNS Record Types

1. **A Record**
   - Maps a **domain** to an **IPv4 address**.
   - Example: `example.com → 192.168.1.1`

2. **AAAA Record**
   - Maps a **domain** to an **IPv6 address**.
   - Example: `example.com → 2001:0db8:85a3::8a2e:0370:7334`

3. **CNAME Record (Canonical Name)**
   - Alias for another domain name.
   - Example: `www.example.com → example.com`

4. **MX Record (Mail Exchange)**
   - Directs **email traffic** to mail servers.
   - Example: `example.com → mail.example.com`

5. **TXT Record**
   - Holds text information for verification and additional info.
   - Common uses:
     - Domain ownership verification (Google, AWS, Azure).
     - Email security: **SPF**, **DKIM**, and **DMARC** records.

---

## Additional DNS Records (Good to Know in DevOps)

6. **NS Record (Name Server)**
   - Specifies the authoritative DNS servers for a domain.

7. **PTR Record (Pointer)**
   - Used for **reverse DNS lookup** (IP → Domain).
   - Example: `192.168.1.1 → example.com`

8. **SRV Record (Service Record)**
   - Defines services available in a domain (used in VoIP, SIP, etc.).

9. **SOA Record (Start of Authority)**
   - Contains admin information, refresh times, and zone settings for a domain.

---

## Why Important in DevOps?

10. **A/AAAA Records** → Point domains to application servers (web apps, APIs).  
11. **CNAME Records** → Used for load balancing, CDN mapping (Cloudflare, AWS CloudFront).  
12. **MX/TXT Records** → Critical for email security and authentication.  
13. **NS Records** → Manage delegation between DNS providers (important in cloud migrations).  
14. **Automation** → Infrastructure-as-Code (Terraform, Ansible, Kubernetes) often manages DNS records automatically.  

# 📌 Two-Tier vs Three-Tier Architecture

## 1. Two-Tier Architecture

1. **Definition**  
   - A **client-server** model with **two layers**:  
     - **Client (Presentation Layer)** → User interface (browser, desktop app).  
     - **Server (Data Layer)** → Database (and sometimes business logic).  

2. **Flow**  
   - Client communicates **directly** with the database server.  

3. **Example**  
   - A desktop application connecting directly to a **MySQL** database.  

4. **Advantages**  
   - Easy to build and deploy.  
   - Faster response (no middle layer).  

5. **Disadvantages**  
   - Poor scalability (too many clients overload DB).  
   - Security risk (DB is directly exposed).  
   - Difficult to maintain for large systems.  


## 2. Three-Tier Architecture

1. **Definition**  
   - A **layered model with three tiers**:  
     - **Presentation Layer (UI/Client):** Web browser, mobile app.  
     - **Application Layer (Business Logic):** Web/App server (API, logic).  
     - **Data Layer (Database):** MySQL, PostgreSQL, MongoDB, etc.  

2. **Flow**  
   - Client → Application Server → Database.  

3. **Example**  
   - Web app:  
     - Client = Browser  
     - App Layer = Node.js / Spring Boot / Django  
     - Data Layer = PostgreSQL  

4. **Advantages**  
   - **Scalable** → App servers can be scaled horizontally.  
   - **Secure** → Database is hidden behind the app layer.  
   - **Maintainable** → Clear separation of UI, logic, and data.  
   - **DevOps Friendly** → Easy to containerize (Docker), orchestrate (Kubernetes), and automate with CI/CD.  

5. **Disadvantages**  
   - More complex to deploy/manage.  
   - Slightly more latency (extra layer).  

## 3. Why Important in DevOps

1. **Two-Tier Architecture**
   - Simple to build and manage, but rarely used in modern DevOps setups.
   - Works for **small-scale apps** where only a few clients connect directly to the database.
   - Example: A simple internal inventory app where 10–20 employees directly connect to a MySQL database.
   - **DevOps Limitation:** 
     - Hard to apply CI/CD pipelines since logic is mixed between client and DB.  
     - No clear separation of concerns.  
     - Scaling is nearly impossible — if 1,000+ users connect, the DB crashes.  


2. **Three-Tier Architecture**
   - The **standard model for cloud-native applications**.
   - Each tier is **decoupled**, making it easier for DevOps to deploy, scale, monitor, and automate.  

   ### In DevOps Context:
   - **Presentation Layer (UI):**
     - Served through **CDN** (Content Delivery Network) for global performance.  
     - Web servers like **Nginx** or **Apache** handle requests.  
     - DevOps tasks: Configure load balancing, caching, HTTPS certificates (LetsEncrypt, AWS ACM).  

   - **Application Layer (Business Logic):**
     - Runs in **containers** (Docker) or directly on app servers (Node.js, Java, Python, etc.).  
     - Managed and scaled by **Kubernetes / Docker Swarm / ECS**.  
     - DevOps tasks: CI/CD pipelines build and deploy containers automatically. Monitoring tools (Prometheus, Grafana, ELK) track app health.  

   - **Database Layer (Data Storage):**
     - Usually not deployed manually — instead use **managed services**:
       - AWS RDS (MySQL, PostgreSQL, MariaDB)  
       - Azure SQL Database  
       - MongoDB Atlas (NoSQL)  
     - DevOps tasks: Ensure backups, replication, failover, and performance tuning. Infrastructure-as-Code (Terraform, Ansible) provisions DBs automatically.  

### 📌 Example in DevOps Workflow
- **Frontend (Presentation):** React app deployed on AWS S3 + CloudFront (CDN).  
- **Backend (Application):** Node.js app containerized in Docker, deployed on Kubernetes (EKS).  
- **Database (Data):** PostgreSQL on AWS RDS with automated backups.  
- **DevOps Pipeline:**  
  - Code pushed to GitHub → Jenkins/GitHub Actions → Build Docker image → Push to Docker Hub/ECR → Deploy to Kubernetes → Update service.  

This separation allows DevOps engineers to:  
- Deploy changes frequently without downtime.  
- Scale different tiers independently (e.g., scale app servers, not DB).  
- Ensure high availability and disaster recovery.  
