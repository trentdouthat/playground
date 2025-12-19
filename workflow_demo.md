Applied Prompt Engineering

**Prompt 1:**
Act as a Senior Cloud Architect. Read the input text below and extract the **Current State**, **Future State**, and **Constraints** into a bulleted list.

**Input:  (The "Client" Email):**
"We are migrating our legacy monolith to Azure. Currently, we have a Java app running on an on-prem Tomcat server connecting to an Oracle DB. We want to move this to Azure Kubernetes Service (AKS) for the app and Azure SQL for the database. We need to handle 10k concurrent users. We are worried about latency between the app and DB. Also, the security team says we can't expose the database to the public internet, but developers need access from home."

**Output 1:**

Here is the architectural summary based on the client email:

### **Architecture Migration Summary**

**Current State (As-Is)**

- **Application:** Java-based monolithic application.
- **Hosting:** On-premises Tomcat server.
- **Database:** Oracle Database (On-prem).

**Future State (To-Be)**

- **Platform:** Microsoft Azure.
- **Compute:** Azure Kubernetes Service (AKS) for the application.
- **Database:** Azure SQL Database.

**Constraints & Requirements**

- **Scalability:** Must support 10,000 concurrent users.
- **Performance:** Low latency required between Application (AKS) and Database (Azure SQL).
- **Security:** Database must **not** be exposed to the public internet (Private connectivity only).
- **Operational Access:** Developers require remote access (work from home) to the database/environment despite the public internet restriction.

**Prompt 2:**
Review the architecture summary above. Identify 3 critical risks related to **Security** and **Performance**.

**Output 2:**

Based on the architecture summary, here are the 3 critical risks identified:

### **Gap Analysis: Critical Risks**

1. **Security Risk: Insecure Remote Access Strategy**
    - **Context:** The security team mandates "no public internet exposure" for the database, but developers need access from home.
    - **Risk:** Attempting to whitelist individual home IP addresses on the Azure SQL firewall is unmanageable and insecure. Without a secure tunnel (VPN/Bastion), developers cannot access the private database, or worse, the team might accidentally expose the SQL endpoint publicly to solve the connectivity issue.
2. **Performance Risk: App-to-Database Network Latency**
    - **Context:** Moving from an on-prem deployment (where App and DB are often on the same rack or switch) to a distributed cloud environment (AKS and Azure SQL).
    - **Risk:** Legacy Java monoliths often have "chatty" database interactions (making many small queries per request). In the cloud, the increased network distance between the AKS cluster and Azure SQL could cause significant performance degradation compared to the on-prem wire speed.
3. **Performance Risk: Connection Exhaustion at Scale**
    - **Context:** Handling 10,000 concurrent users.
    - **Risk:** A legacy Tomcat application may rely on persistent connections or inefficient connection pooling. Azure SQL Database has strict limits on sessions and workers (depending on the tier). 10k concurrent users could easily exhaust the database connection pool, leading to timeouts and service outages (Throttling).
    

**Prompt 3:**
Propose a specific Azure native solution for each of the 3 risks identified below.
**Constraint:** Output format must be JSON: `[{"risk": "string", "solution": "string", "azure_service": "string"}]`

**Input:** [Paste the 3 risks identified above]

**Output 3:**

JSON

`[
  {
    "risk": "Security Risk: Insecure Remote Access Strategy",
    "solution": "Implement a Point-to-Site (P2S) VPN strategy to allow developers to securely tunnel into the Azure Virtual Network from their remote locations without exposing the database public endpoint.",
    "azure_service": "Azure VPN Gateway"
  },
  {
    "risk": "Performance Risk: App-to-Database Network Latency",
    "solution": "Implement a 'Cache-Aside' pattern to store frequently accessed data in memory, significantly reducing the number of round-trip network calls between the AKS application and the Azure SQL Database.",
    "azure_service": "Azure Cache for Redis"
  },
  {
    "risk": "Performance Risk: Connection Exhaustion at Scale",
    "solution": "Migrate to the vCore-based purchasing model (specifically Business Critical or Hyperscale tiers) which offers significantly higher limits for maximum concurrent workers and logins compared to DTU models, accommodating the high concurrency of legacy connection pooling.",
    "azure_service": "Azure SQL Database (vCore Business Critical/Hyperscale)"
  }
]`
