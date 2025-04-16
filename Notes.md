## AZ-900 Microsoft Azure Fundamentals Study Notes

**☁️ Domain 1: Describe Cloud Concepts (Approx. 25-30%)**

**1. What is Cloud Computing?**

- **Formal Definition (NIST):** On-demand network access to a shared pool of configurable computing resources (like networks, servers, storage, apps, services) that can be quickly set up with minimal management effort.
- **Microsoft's View:** Delivering computing services (servers, storage, databases, networking, software, analytics, intelligence) over the Internet ("the cloud"). It expands traditional IT capabilities (like IoT, ML, AI) and allows businesses to grow without building and managing their own physical datacenters.

**2. Shared Responsibility Model**

- **Concept:** Defines who is responsible for what between the Cloud Service Provider (CSP) like Microsoft Azure and you (the Customer).
- **Responsibilities Breakdown:**
  - **✅ Customer ALWAYS Responsible For:**
    - Information and Data
    - Devices (Mobiles, PCs accessing the cloud)
    - Accounts and Identities
  - **🔄 Varies Depending on Service Model (IaaS, PaaS, SaaS):**
    - Applications
    - Network Controls
    - Operating System
  - **☁️ Cloud Provider ALWAYS Responsible For (in Public Cloud):**
    - Physical Hosts (Servers)
    - Physical Network Infrastructure
    - Physical Datacenter Security
- **Key Trend:** As you move from IaaS → PaaS → SaaS, the Cloud Provider takes on _more_ responsibility.

**3. Cloud Models (Deployment Types)**

- **☁️ Public Cloud:**
  - **What:** Resources owned and operated by a CSP (like Azure), accessed over the public internet.
  - **Benefits:** High scalability & agility, Pay-As-You-Go (PAYG) pricing, no hardware maintenance for users, lower technical skills barrier.
  - **Use Case:** Organizations wanting to offload infrastructure management, leverage cloud scalability, and avoid building their own datacenter.
- **🏢 Private Cloud:**
  - **What:** Resources used exclusively by a single organization. Can be located in the organization's own datacenter or hosted by a third party.
  - **Benefits:** Maximum control over resources, meets specific security or compliance requirements, supports legacy systems.
  - **Use Case:** Organizations needing high control, strict compliance adherence, or specific security configurations.
- **🔄 Hybrid Cloud:**
  - **What:** Combines Public and Private clouds, allowing data and applications to be shared between them.
  - **Benefits:** Flexibility to balance needs (e.g., keep sensitive data private, use public cloud for scalable apps), cost optimization, supports gradual cloud migration.
  - **Use Case:** Organizations wanting the best of both worlds – control for sensitive assets, scalability for others.

**4. Core Cloud Benefits & Concepts**

- **📈 High Availability (HA):** Keeping services operational and accessible for extended periods, minimizing downtime. Measured in percentages (e.g., 99.9%, 99.99%). Focuses on resilience against _service-level_ failures.
- **↔️ Scalability:** Ability to adjust resources (compute, storage, network) to meet changing needs.
  - _Vertical Scaling (Scaling Up/Down):_ Adding/removing power (CPU, RAM) to existing instances.
  - _Horizontal Scaling (Scaling Out/In):_ Adding/removing more instances of a resource.
  - Handles _long-term growth or planned capacity changes_.
- **⚙️ Elasticity:** The ability to _automatically_ and quickly scale resources up or down in response to _fluctuating demand_ or load. Handles _short-term spikes or unpredictable changes_.
- **🚀 Agility:** The ability to react quickly – rapidly deploying, configuring, and adapting resources as business needs change.
- **🛡️ Fault Tolerance:** A system's ability to continue operating even if some components (like a disk, power supply, server) fail. Achieved through redundancy.
- **🌊 Disaster Recovery (DR):** Procedures and technologies to recover services after a major catastrophic event (e.g., entire datacenter or region failure).
- **💯 Reliability:** Combines HA and Fault Tolerance. It's the overall ability of a system to recover from failures and remain functional. Includes:
  - _Resiliency:_ Ability to return to full function after a failure occurs.
  - _Availability:_ Ensuring consistent access to services.
- **🔮 Predictability:** Having confidence in cost estimation and performance consistency.
- **🔒 Security:** Protecting cloud assets (data, applications, infrastructure). This is a _shared responsibility_. Azure provides built-in features like DDoS protection.
- **📜 Governance:** Establishing rules, policies, and processes to ensure compliance, security standards, cost optimization, and operational consistency (e.g., using Azure Policy, Cloud Adoption Framework).
- **🛠️ Manageability:** Ease of managing cloud resources.
  - _What can be managed:_ Monitoring, alerts, auto-scaling configurations.
  - _How resources are managed:_ Using tools like the Azure Portal, CLI, PowerShell, APIs. Cloud providers also manage underlying infrastructure (e.g., patching OS in PaaS).
- **💰 Economies of Scale:** The cost savings cloud providers achieve by operating at a massive scale, which they pass on to customers as lower prices.

**5. Cloud Expenditure Models**

- **🏗️ CapEx (Capital Expenditure):** Upfront investment in physical infrastructure (e.g., servers, buildings). Common in on-premises models. _Reduced by cloud adoption._
- **💸 OpEx (Operational Expenditure):** Ongoing spending on services or products based on usage (e.g., monthly cloud bill). Common in public cloud models. _Increased by cloud adoption._
- **Key Shift:** Cloud computing generally shifts IT spending from CapEx to OpEx.

**6. Cloud Pricing Models**

- **💧 Consumption-based (Pay-As-You-Go - PAYG):** Pay only for the resources you actually consume (e.g., per hour for VMs, per GB for storage, per execution for functions).
- **🏷️ Fixed Price:** Pay a set amount for a service or resource reservation, often regardless of exact usage (e.g., Reserved Instances, some software licenses). Provides cost predictability.

**7. Serverless Computing**

- **Concept:** An abstraction layer where the cloud provider fully manages the server infrastructure. Developers focus solely on writing and deploying code (functions).
- **Characteristics:**
  - Event-driven (code runs in response to triggers).
  - Instant, automatic scaling based on demand.
  - Pay only for execution time/resources used during execution.
  - Often stateless (doesn't retain memory between executions) and ephemeral (short-lived).
- **Serverless vs. PaaS:**
  - _Serverless:_ Less infrastructure control, inherently auto-scales, often faster startup for individual functions.
  - _PaaS:_ More control over the environment, scaling needs explicit configuration, might have longer startup for the platform itself.
- **Key Azure Serverless Services:**
  - **⚡ Azure Functions:** Execute small pieces of code (functions) triggered by events (FaaS - Function as a Service). Pay per execution/resource consumption.
  - **🔗 Azure Logic Apps:** Visually design, build, and automate workflows that integrate apps, data, services, and systems using pre-built connectors. Foundation for Power Automate.
  - **📣 Azure Event Grid:** A fully managed event routing service using a publish/subscribe model. Connects event sources (e.g., Blob Storage creation event) to event handlers (e.g., Azure Functions, Logic Apps). Enables reactive, event-driven architectures. Pay per event processed.

**8. Data Types (Relevant for Storage Choices)**

- **📄 Unstructured Data:** No defined format or organization (e.g., photos, videos, audio files, text documents, log files). _Ideal for Blob Storage._
- **📊 Structured Data:** Highly organized data that fits neatly into rows and columns with a defined schema (e.g., database records, financial data). _Ideal for SQL Databases, Azure Table Storage._

---

**🏗️ Domain 2: Describe Azure Architecture and Services (Approx. 35-40%)**

**1. Core Azure Architectural Components**

- **🗺️ Azure Geography:** A discrete market, typically containing two or more Regions, that preserves data residency and compliance boundaries (e.g., United States, Europe, Asia Pacific).
- **📍 Azure Region:** A geographical area containing one or more datacenters connected by a low-latency network. Services are deployed _into specific regions_. (e.g., East US, West Europe).
- **🤝 Region Pairs:** Two regions within the same geography (usually >300 miles apart) paired for disaster recovery purposes. Benefits include prioritized recovery and sequential platform updates.
- **🏛️ Sovereign Regions:** Special Azure regions designed to meet strict compliance or legal requirements, operated by specific entities (e.g., Azure Government for US government agencies, Azure China). Physically and logically isolated from other Azure regions.
- **🏢 Availability Zones (AZs):** Physically separate locations _within a single Azure region_. Each AZ has independent power, cooling, and networking. Protects applications and data from datacenter-level failures. Services can be deployed as "Zone-redundant".
- **🏬 Datacenters:** The physical buildings containing servers, networking equipment, and backed by redundant power, cooling, and network connectivity. Regions contain multiple datacenters; AZs are composed of one or more datacenters.
- **ιεράρχηση Azure Resource Hierarchy (Scopes for Management & Policy):**
  - **👑 Management Groups:** Group multiple Subscriptions for unified policy application and access management. A root Management Group exists by default.
  - **💳 Subscriptions:** A unit for billing, management, and scale limits. Acts as a container for Resource Groups and resources.
  - **📦 Resource Groups (RGs):** Logical containers for grouping related Azure resources that share a common lifecycle (deployed, managed, and deleted together). A resource must belong to exactly one RG.
  - **⚙️ Resources:** Individual manageable items within Azure (e.g., Virtual Machine, Storage Account, Virtual Network, Database).

**2. Azure Compute Services (Running Code/Applications)**

- **🖥️ Azure Virtual Machines (VMs):** Infrastructure as a Service (IaaS). Rent virtual servers in the cloud. Provides full control over the Operating System (OS).
  - _Needs:_ Virtual Disk for OS/data, Virtual Network (VNet) and Network Interface Card (NIC) for connectivity, Network Security Group (NSG) for basic firewalling, optional Public IP address.
- **➕➖ Azure VM Scale Sets (VMSS):** Manage and automatically scale a group of identical load-balanced VMs. Ideal for applications needing to handle varying loads. _Focus: Automatic Scaling._
- **🏢🏢 Azure VM Availability Sets:** Protect applications from hardware failures or planned maintenance _within a single datacenter_. Distributes VMs across:
  - _Fault Domains (FDs):_ Groups of VMs sharing common hardware (power, network switch). Protects against hardware failure.
  - _Update Domains (UDs):_ Groups of VMs that may be rebooted together during planned maintenance. Protects against maintenance downtime.
  - _Focus: Resiliency within a Datacenter._
- **💻 Azure Virtual Desktop (AVD):** Managed Desktop as a Service (DaaS) / Virtual Desktop Infrastructure (VDI). Delivers Windows 10/11 desktops and applications hosted in Azure.
- **📦 Azure Container Instances (ACI):** Run single Docker containers quickly without managing underlying VMs or orchestrators. A simple, serverless way to run containers.
- **🚢 Azure Kubernetes Service (AKS):** Managed Kubernetes container orchestration service. Simplifies deploying, managing, and scaling containerized applications. You pay primarily for the agent nodes (VMs running your containers). _Use Case: Complex, production-grade container management._
- **⚡ Azure Functions:** (See Serverless in Domain 1). Event-driven code execution (FaaS).
- **🌐 Azure App Service:** Platform as a Service (PaaS) for building, deploying, and scaling web apps, APIs, and mobile back ends quickly. Supports various languages and frameworks.
  - _Includes:_ Web Apps (hosting websites), API Apps (hosting APIs), WebJobs (running background tasks), Mobile Apps (mobile app back ends).

**3. IaaS, PaaS, SaaS - Common Use Cases**

- **🔧 IaaS (e.g., VMs):** Migrating existing on-prem apps ("lift and shift"), Dev/Test environments, applications with fluctuating demand, datacenter extension (Hybrid), Disaster Recovery sites.
- **🛠️ PaaS (e.g., App Service, SQL Database):** Accelerating development (provides frameworks/services), Business Analytics / Business Intelligence, scenarios where managing the underlying OS/infrastructure is not desired.
- **✉️ SaaS (e.g., Microsoft 365, Salesforce):** Email and collaboration tools, Customer Relationship Management (CRM), finance/expense tracking – outsourcing common business functions.

**4. Azure Networking Services (Connecting Resources)**

- **🌐 Azure Virtual Network (VNet):** Your own private network space in Azure. Provides logical isolation for your resources. Segmented into one or more _subnets_.
- **➗ Subnets:** Divisions of a VNet's IP address range. Azure resources (like VMs) are deployed _into_ subnets. By default, resources within different subnets _in the same VNet_ can communicate.
- **🔗 VNet Peering:** Connects two Azure VNets (can be in the same or different regions), allowing resources in them to communicate directly as if they were in the same network.
- **🔒 VPN Gateway:** Creates secure, encrypted connections (tunnels) between an Azure VNet and an on-premises network (Site-to-Site VPN) or individual users (Point-to-Site VPN) over the _public internet_. Key component for _hybrid cloud connectivity_.
- **🚀 ExpressRoute:** Provides a private, dedicated, high-throughput connection between your on-premises network and Azure through a connectivity partner. _Does not use the public internet_. Offers higher reliability, speed, and lower latency than VPN Gateway. Also key for _hybrid cloud connectivity_.
- **🌍 Azure DNS:** Service for hosting your public DNS domains (like `yourcompany.com`) or private DNS zones within your VNet.
- **🚪 Service Endpoint:** Secures specific Azure service resources (like Storage Accounts, SQL Databases) by allowing access _only_ from designated VNet subnets. Traffic travels over an optimized path on the Azure backbone network. Restricts _outbound access from the VNet_ to _all instances_ of the targeted service type (e.g., all Storage Accounts in a region).
- **🔑 Private Endpoint:** Exposes a specific Azure service instance (e.g., _one specific_ Storage Account or SQL Database) using a _private IP address_ from within your VNet. This enables resources in your VNet (and on-premises via VPN/ExpressRoute) to connect privately and securely to that specific service instance without going over the public internet.

**5. Azure Storage Services (Storing Data)**

- **📦 Azure Blob Storage:** Highly scalable object storage for _unstructured_ data (e.g., documents, images, videos, backups, logs). Offers different access tiers:
  - **🔥 Hot:** Optimized for frequently accessed data. Highest storage cost, lowest access cost.
  - **❄️ Cool:** Optimized for infrequently accessed data (stored for at least 30 days). Lower storage cost than Hot, higher access cost.
  - **🥶 Cold:** Optimized for rarely accessed data (stored for at least 90 days). Lower storage cost than Cool, higher access cost. Suitable for short-term backup/DR. _(Newer tier, previously part of Archive comparison)_
  - **🧊 Archive:** Optimized for rarely accessed data (stored for at least 180 days) with flexible latency requirements (hours). Lowest storage cost, highest access cost and retrieval latency (data is offline). Suitable for long-term backup, archival.
- **💾 Azure Disk Storage:** Persistent block storage (Managed Disks) designed for use with Azure VMs. Options include Standard HDD, Standard SSD, Premium SSD, Ultra Disk, offering different performance/cost levels.
- **📁 Azure Files:** Fully managed file shares in the cloud accessible via standard Server Message Block (SMB) and Network File System (NFS) protocols. Useful for "lift and shift" file share scenarios, shared application settings.
- **📨 Azure Queue Storage:** Service for storing large numbers of messages that can be accessed by applications. Used for decoupling application components and building asynchronous workflows.
- **📋 Azure Table Storage:** A NoSQL key-attribute store for structured, non-relational data. Provides schemaless storage.
- **<0xF0><0x9F><0x94><0x82> Storage Redundancy (Data Protection Options):**
  - **LRS (Locally-redundant storage):** 3 copies of data within a _single physical datacenter_. Lowest cost, but vulnerable to datacenter-level failure.
  - **ZRS (Zone-redundant storage):** 3 copies of data spread across different Availability Zones _within the primary region_. Protects against datacenter failure.
  - **GRS (Geo-redundant storage):** LRS in the primary region (3 copies) + asynchronous replication to a _secondary region_ (3 copies). Protects against regional disasters. Read access to secondary (RA-GRS) is optional.
  - **GZRS (Geo-zone-redundant storage):** ZRS in the primary region (3 copies across AZs) + asynchronous replication to a _secondary region_ (LRS - 3 copies in one DC). Provides highest level of durability combining AZ and regional protection. Read access to secondary (RA-GZRS) is optional.

**6. Data Migration & Movement Tools**

- **⌨️ AzCopy:** Command-line utility for copying data to/from Azure Blob, File, and Table storage.
- **🖱️ Azure Storage Explorer:** GUI application for managing Azure storage resources (Blobs, Files, Queues, Tables) on Windows, macOS, and Linux.
- **🔄 Azure File Sync:** Centralize your organization's file shares in Azure Files while keeping the flexibility, performance, and compatibility of an on-premises file server. Caches data locally.
- **✈️ Azure Migrate:** A central hub of tools for discovering, assessing, and migrating on-premises servers, apps, and data to Azure.
- **🚚 Azure Data Box:** Physical appliances (various sizes) shipped to you for transferring large amounts of data to Azure when network transfer is impractical (offline transfer).

**7. Azure Identity, Access, and Security**

- **🔑 Authentication (AuthN):** The process of proving you are who you say you are. Verifying identity.
- **📜 Authorization (AuthZ):** The process of determining what an authenticated user is allowed to do. Granting permissions.
- **🆔 Microsoft Entra ID (formerly Azure Active Directory / Azure AD):** Microsoft's cloud-based identity and access management service. Manages users, groups, application access, enables Single Sign-On (SSO), Multi-Factor Authentication (MFA), etc.
- **🔐 Authentication Methods in Entra ID:**
  - **SSO (Single Sign-On):** Log in once to access multiple applications/services.
  - **MFA (Multi-Factor Authentication):** Requires two or more verification factors:
    - Something you _know_ (password, PIN)
    - Something you _have_ (authenticator app, physical token, phone call/SMS)
    - Something you _are_ (biometrics like fingerprint, face scan)
  - **Passwordless:** Sign-in without a password using methods like:
    - Windows Hello for Business (biometrics/PIN on device)
    - FIDO2 Security Keys (physical USB/NFC keys)
    - Microsoft Authenticator App (phone sign-in notification)
  - _Note:_ OATH Tokens (Hardware or Software time-based codes) are a type of "Something you have" factor for MFA.
- **👥 External Identities (Connecting with users outside your org):**
  - _B2B Collaboration:_ Invite guest users into your tenant to collaborate.
  - _B2B Direct Connect:_ Establish mutual trust with another Entra ID tenant (e.g., for shared Teams channels).
  - _Azure AD B2C:_ Identity management solution for customer-facing applications.
- **🚦 Conditional Access:** Entra ID feature using If-Then policies. If a user meets certain conditions (Signal: e.g., user location, device health, application accessed), then enforce specific controls (Action: e.g., require MFA, block access, limit session).
- **👑 Azure RBAC (Role-Based Access Control):** Manages authorization for _Azure resources_. Grants permissions by assigning roles to users, groups, or service principals at specific scopes (Management Group, Subscription, Resource Group, Resource). Enforces the principle of _least privilege_.
  - _Components:_ Security Principal (who), Role Definition (what permissions), Scope (where).
- **🛡️ Zero Trust Model:** Security strategy assuming breaches are inevitable. Core principles:
  - _Verify Explicitly:_ Always authenticate and authorize based on all available data points.
  - _Use Least Privilege Access:_ Grant only the permissions needed, just-in-time and just-enough.
  - _Assume Breach:_ Minimize blast radius; segment access; use analytics to detect threats.
  - _Applies across:_ Identities, Devices, Applications, Data, Infrastructure, Network.
- **🧅 Defense in Depth:** A layered security approach. If one layer fails, the next layer provides protection. Layers typically include: Physical Security -> Identity & Access -> Perimeter -> Network -> Compute -> Application -> Data.
- **☁️🛡️ Microsoft Defender for Cloud:** Provides Security Posture Management (CSPM) and Cloud Workload Protection (CWPP).
  - _CSPM:_ Assesses security configuration, provides recommendations (Secure Score).
  - _CWPP:_ Provides threat detection and protection for Azure, on-premises, and multi-cloud resources (VMs, containers, databases, etc.).
- **🧱 Network Security Groups (NSGs):** Act like a basic, stateful firewall for Azure resources. Filters inbound/outbound network traffic to/from Azure resources (like VM NICs or subnets) based on 5-tuple rules (Source IP, Source Port, Destination IP, Destination Port, Protocol).
- **🔥 Azure Firewall:** A managed, cloud-native, stateful firewall service with built-in high availability and scalability. Offers more advanced features than NSGs (e.g., application-level filtering, threat intelligence).
- **🌊 Azure DDoS Protection:** Protects Azure resources against Distributed Denial of Service (DDoS) attacks.
  - _Basic Tier:_ Free, automatically enabled, protects Azure platform infrastructure.
  - _Standard Tier:_ Paid service, provides enhanced protection specifically for your VNet resources, includes tuning, alerting, metrics, and cost protection.

---

**📊 Domain 3: Describe Azure Management and Governance (Approx. 30-35%)**

**1. Cost Management & Optimization**

- **💲 Factors Affecting Cost:**
  - **Resource Type:** Different services have different pricing structures (e.g., VMs vs. Storage).
  - **Services Consumed:** Usage metrics (e.g., compute hours, data stored, operations performed).
  - **Location (Region):** Costs can vary significantly between Azure regions.
  - **Bandwidth:** Data transfer costs. _Ingress_ (data going into Azure) is generally free. _Egress_ (data going out of Azure) often incurs charges.
- **💰 Cost Reduction Strategies:**
  - **Reserved Instances (RIs) / Savings Plans:** Commit to use specific compute resources (like VMs) for 1 or 3 years for significant discounts compared to PAYG.
  - **Reserved Capacity:** Similar commitment model for certain PaaS services (e.g., SQL Database vCores, Cosmos DB RU/s).
  - **Azure Hybrid Benefit:** Use your existing on-premises Windows Server / SQL Server licenses (with active Software Assurance) to get discounts on Azure VMs and SQL services (Bring Your Own License - BYOL).
  - **Spot VMs / Spot Instances:** Utilize unused Azure compute capacity at very deep discounts, but workloads can be interrupted (preempted) with short notice. Ideal for fault-tolerant, non-critical workloads.
- **🛠️ Cost Management Tools:**
  - **🔢 Pricing Calculator:** Estimate the cost of Azure services _before_ deploying them.
  - **⚖️ TCO (Total Cost of Ownership) Calculator:** Compare the estimated costs of running your workloads on-premises versus in Azure _before_ migrating.
  - **📈 Azure Cost Management + Billing:** Track, analyze, and optimize Azure spending _after_ resources are deployed. Features include cost analysis, budget creation, alerts, and cost-saving recommendations.
- **🏷️ Tags:** Key-value pairs applied to Azure resources. Used for organizing, managing, filtering, and tracking costs (e.g., tag by department, project, environment).

**2. Azure Governance Features (Enforcing Rules & Standards)**

- **🔍 Microsoft Purview (formerly Azure Purview):** A unified data governance service. Helps discover, classify, map, and manage data across your entire estate (Azure, on-prem, multi-cloud).
- **📜 Azure Policy:** Enforces organizational standards and assesses compliance at scale. Define rules (policies) that resources must adhere to. Can:
  - Audit resource configurations.
  - Deny creation of non-compliant resources.
  - Modify resources to make them compliant.
  - Deploy required configurations (e.g., via ARM templates).
  - Policies are often grouped into _Initiatives_ (Policy Sets) for easier assignment.
- **🏗️ Azure Blueprints:** Allows defining a repeatable set of Azure resources that adheres to organization standards, patterns, and requirements. Packages artifacts like:
  - Resource Groups
  - ARM Templates (for deploying resources)
  - Policy Assignments
  - Role Assignments (RBAC)
  - Often used to quickly set up _new, governed environments_ consistently.
- **🔒 Resource Locks:** Protect Azure resources from accidental deletion or modification. Applied at a specific scope (Subscription, RG, Resource).
  - `CanNotDelete`: Authorized users can read/modify, but not delete.
  - `ReadOnly`: Authorized users can only read, cannot modify or delete.
  - _Locks override user permissions (even owners)._
- **🗺️ Cloud Adoption Framework (CAF) for Azure:** Microsoft's documented guidance, best practices, and tools to help organizations successfully adopt Azure. Covers strategy, planning, readiness, migration, governance, and management.

**3. Managing and Deploying Azure Resources**

- **🛠️ Management Interfaces:**
  - **🖱️ Azure Portal:** Web-based graphical user interface (GUI).
  - **💻 Azure PowerShell:** Command-line shell and scripting language using .NET cmdlets.
  - **⌨️ Azure CLI (Command-Line Interface):** Cross-platform command-line tool using Bash-like commands.
  - **☁️ Azure Cloud Shell:** Browser-accessible, authenticated shell (choose PowerShell or Bash) with common tools pre-installed.
  - **📱 Azure Mobile App:** Manage resources on the go from iOS or Android devices.
- **⚙️ Azure Resource Manager (ARM):** The deployment and management service for Azure. Provides a consistent management layer. All management tools interact with the ARM API. Key features:
  - Handles resource deployment, updates, deletion.
  - Enables declarative templates (Infrastructure as Code).
  - Provides dependency management, RBAC, tagging, activity logs.
- **📄 Infrastructure as Code (IaC):** Managing and provisioning infrastructure (networks, VMs, etc.) through machine-readable definition files (code), rather than physical hardware configuration or interactive tools. Key DevOps practice enabling automation, consistency, and repeatability.
  - **📝 ARM Templates:** Native Azure IaC format using JSON. Define the resources, configurations, and dependencies needed for a deployment. They are _declarative_ (define desired end state) and _idempotent_ (running the same template multiple times results in the same state).
- **🔗 Azure Arc:** Extends Azure management capabilities (like ARM, Azure Policy, monitoring, security via Defender for Cloud) to resources located _outside_ of Azure – on-premises servers (Windows/Linux), Kubernetes clusters, databases, edge devices, and even resources in other public clouds. Provides a single pane of glass for managing hybrid and multi-cloud environments.

**4. Azure Monitoring Tools (Observability)**

- **📊 Azure Monitor:** The central, unified platform in Azure for collecting, analyzing, and acting on telemetry data (metrics and logs) from your Azure and on-premises environments. Key components include:
  - **🪵 Log Analytics Workspace:** The primary data store for logs collected by Azure Monitor. Logs can be queried using the Kusto Query Language (KQL).
  - **🔔 Azure Monitor Alerts:** Proactively notify you or trigger automated actions (e.g., run an Azure Function, call a webhook) when specific conditions are met based on metrics, logs, Activity Log events, or Service Health status.
  - **💡 Application Insights:** An Application Performance Management (APM) feature _within_ Azure Monitor. Provides deep insights into application performance, usage, availability, and failures. Collects telemetry like request rates, response times, exceptions.
- **👨‍⚕️ Azure Advisor:** Provides personalized recommendations based on your Azure usage to help you optimize your resources across five pillars:
  - Cost
  - Security
  - Reliability (formerly High Availability)
  - Performance (formerly Performance Efficiency)
  - Operational Excellence
- **🩺 Azure Service Health:** Informs you about Azure platform issues that could potentially affect _your_ services. Includes:

  - _Service Issues:_ Current problems in Azure (outages).
  - _Planned Maintenance:_ Upcoming maintenance events.
  - _Health Advisories:_ Issues requiring your action (e.g., service retirements).

- **📜 Activity Log:** Provides a record of all operations performed on resources in your subscription. Useful for auditing and troubleshooting.
- **🔍 Resource Health:** Provides information about the health of your individual Azure resources. Helps you understand if a resource is 🟢 healthy, 🟠 degraded, or 🔴 unavailable.

- **🛠️ Azure Support Plans:** Different levels of support (Basic, Developer, Standard, Professional Direct) with varying response times and support channels (📧 email, 📞 phone, 💬 chat).
  - **Basic:** Free.
  - **Developer, Standard, Professional Direct:** Paid plans with enhanced support options.
- **🔑 Azure Service Level Agreements (SLAs):** Guarantees the availability and performance of Azure services. SLAs are service-specific and define the percentage of uptime you can expect. If Azure fails to meet the SLA, you may be eligible for service credits.
- **📜 Azure Service Level Objectives (SLOs):** Specific measurable characteristics of a service (e.g., availability, performance) that contribute to the overall SLA. SLOs are often defined in terms of error rates, latency, and throughput.
- **📈 Azure Service Level Indicators (SLIs):** Metrics used to measure the performance of a service against its SLOs. Examples include request latency, error rates, and availability percentages.
