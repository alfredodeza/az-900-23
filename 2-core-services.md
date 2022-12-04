LP: https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-azure-services/

## Azure Compute Services
LM: https://docs.microsoft.com/en-us/learn/modules/azure-compute-fundamentals/

### Virtual Machines (VMs)

Definition: Emulate physical machines. These provide IaaS.

### Virtual machine scale sets

Definition: Deploy and manage set of identical VMs. Supports autoscale

### Containers and K8s

Definition: Azure compute resources that you can use to deploy+manage containers. Quickly create, scale, and stop dynamically.

### Azure App Service

Definition: a Paas that allows to build, deploy, and scale web/mobile/API apps on any platform.

Types:

* Web apps
* API apps
* Webjobs (for background tasks)
* Mobile apps

Service handles:

* Deployment and management
* Can secure endpoints
* Scaling of sites
* Built-in load balancing and traffic manager

### Azure Functions

Definition: Serverless code that does not require managing the underlying platform.

Similar to Azure Logic Apps. Both are serverless.

Use them for:

* Running on a timer
* Trigger over HTTP
* With queues.

Key difference with Azure Logic Apps: Functions requires code and is not an orchestration service

### When to use VMs

* Total control of the OS
* To use custom Software
* Custom hosting configurations

Example scenarios:

* In testing/development
* When extending your datacenter to the cloud
* For disaster recovery (quickly provisioning VMs)


### Azure Batch

Definition: Allows large-scale parallel and high-performance computing (HPC) batch jobs. Can scale to thousands of VMs

Batch can:

* Start a pool of compute
* Install apps + stage data
* Run jobs
* Identify failures
* Reque work
* Scale down

### Azure Logic Apps

Definition: It executes workflows, designed to automate (orchestrate) business scenario from predefined logic blocks

Similar to Functions. Both can get triggered with logic based on event.

Workflows are persisted in JSON.

Declarative and stateful. Runs only in the cloud.

Key difference with Azure Functions: Logic Apps don't require code, and it is an orchestration service

### Azure Virtual Desktop

Definition: A Windows desktop virtualization service in the cloud.

Works across devices like Windows, Mac, iOS, Android, and Linux. Including most browsers

Use it because:

* Provides flexibility (supported across devices)
* Enhanced security. Data+apps are separate from the local hardware

* **Simplified management**: with Azure AD + RBAC
* **Performance management**: Can load balance on VM host pools
* **Multi-session**: Allows concurrent users on Windows 10

Reduce costs by bringing your own licenses. Available with no extra costs for existing MSFT 365 license.
Save on compute by buying 1 or 3 year Azure reserved virtual machine instances.

## Azure Networking
LM https://docs.microsoft.com/en-us/learn/modules/azure-networking-fundamentals/

### Azure Virtual Network fundamentals

* Isolate
* Communicate over the internet
* Communicate between Azure resources
* Communicate with on-premise
* Route+filter traffic
* Connect virtual networks

**Internet communications**: VMs can connect to the internet _by default_

**Communicate between Azure resources**: with Virtual networks, or service endpoints (from an Azure resource)

**Communicate with on-premise**:
 * via Point-to-site (typical VPN)
 * Site-to-site (everything appears on the same network)
 * Azure ExpressRoute: dedicated private connection to Azure (not over the internet)

**Route Network traffic**
* Route tables: defines rules for directing network traffic
* Border Gateway Protocol: (BGP) Propagate on-premises BGP to Azure virtual networks

**Connect virtual networks**: With network peering. Peering allows connecting virtual networks together.

## Azure VPN gateway fundamentals


### VPN Gateway

Definition: A type of virtual network gateway.

They enable:

* Connecting on-premise datacenter to virtual networks (site-to-site)
* Connecting individual devices to virtual networks (point-to-site)
* Connect virtual networks to other virtual networks (network-to-network)

**Only 1 VPN gateway per virtual network**

Supports two types:

**Policy-based**
* IKEv1 only
* Static-routing: Combinations of address prefixes control traffic. Source+destination are declared in policy (**not** in routing tables)
* Mainly used for compatibility with legacy VPN

**Route-based**
Use it for:
* point-to-site, connections between virtual networks, multisite, coexistence with Azure ExpressRoute
* IKEv2 support
* Wildcard (any-to-any) traffic selectors
* Dynamic routing protocols. Source/Destination networks don't need to be statically defined. Supports Border Gateway Protocol (BGP)

**Gateway sizes**
* Basic (does not support Border Gateway Protocol)
* VpnGw1
* VpnGw2
* VpnGw3

**Required Azure resources**
* Virtual Network
* Gateway subnet
* Public IP
* Local network gateway
* Virtual network gateway
* Connection resource

### HA for VPN gateways

* **Active/Standby**: By default VPN gateways are deployed as two instances. Automatic failover. Connections can be interrupted
* **Active/Active**: Use with Border Gateway Protocol, create each VPN with unique IPs but separate tunnels from on-premise device.
* **ExpressRoute Failover**: If an ExpressRoute connection fails, connectivity can fail over to traffic over the internet with the VPN
* **Zone-redundant gateways** For regions that support AZs, VPNs can be deployed with zone-redundancy. Requires a Standard public IP (not a **basic** IP)

## Azure ExpressRoute Fundamentals
LM https://docs.microsoft.com/en-us/learn/modules/azure-networking-fundamentals/express-route-fundamentals

Definition: Extends/connects your on-premise network into Azure over a private connection (**not** over the internet)

Connection types:

* Point-to-Point (between nodes) (L2)
* Any-to-Any (VPN) (L3)

Features:

* Fast (over private fiber optic)
* Low latency
* Higher security
* Global connectivity with ExpressRoute premium
* Reduntant + Dynamic Routing
* Uptime SLA

### Redundancy

Only for Layer 3 connections. Redundancy uses multiple devices for HA

### Connectiviy to cloud services

Direct connection to:

* Compute services like: VMs
* Cloud services like Cosmos DB or Storage

### Dynamic Routing

Uses Border Gateway Protocol (BGP) routing protocol, allowing dymaic routing between on-premise and Azure services


### Connectivity Models

* **Cloud Exchange**: From an ISP/Datacenter to Azure
* **Point-to-Point**: From on-premise to Azure
* **Any-to-Any**: WAN with Azure with L3 connectivity. Access Azure like any private service in a WAN

## Azure Storage Services
LM https://docs.microsoft.com/en-us/learn/modules/azure-storage-fundamentals/

### Disk Storage

Definition: Provides (virtual) disks for Azure VMs. Similar like on-premise server with disks.

Types:

* SSDs
* HDDs
* Premium SSDs
* Ultra Disks

ZERO% annualized failure rate.

### Blob storage

Definition: Unstructured object storage for massive amounts of data.

Features:
* Can be readched anywhere from http
* Does not require space/disk management

Use it for:

* Serve assets over to a browser
* Store files for distributed access
* Video+Audio streaming
* Disaster recovery backups
* Analyzis for on-premise Azure-hosted services
* Storing up to 8TB of data for VMs

Blobs are stored in containers which are owned by an account:

Account -> Many containers (e.g. movies/pictures) -> many blobs (files)

### Azure files

Definition: Is a file share service in the cloud available via SMB (Server Message Block) and NFS (preview) (Network File System).

File shares can be mounted on Windows, Linux and OSX at the same time.

Features:

* Data encrypted at rest.
* Access files from anywhere in the world via a URL
* Provide temporary access with a SAS (Shared Access Signature)


Use it for:

* Seamless support for apps that use SMB that need to be migrated to the cloud
* Store, retrieve, and share configuration files that can be accessed by multiple VMs
* Write metrics, crash dumps, or diagnostic logs, so that they can be analyzed later


### Blob Access Tiers

Definition: Allows organizing data depending on access frequency and retention period.

* **Hot access tier**: Frequently accessed data like website assets
* **Cool access tier**: Infrequent access stored for at least 30 days
* **Archive access tier**: Almost never accessed and stored for at least 180 days, like backups

Service attributes:

* Hot + Cool tiers are set at the account level. Acrhive isn't available at the account level.
* All tiers can be set before or after uploading at the blob level.
* Archive has the lowest cost, but it is more expensive to rehydrate and access data.

Tier cost

| Tier | SLA | Access Cost | Storage Cost |
| -- | -- | -- | -- |
| Hot | High | Low | High |
| Cold | Medium | High | Low |
| Archive | - | Highest | Lowest |

## Azure Database and analytics
LM https://docs.microsoft.com/en-us/learn/modules/azure-database-fundamentals/

### Azure Cosmos DB

Definition: A globally distributed, multi-model database service.

Although usually meant for Key/Value store, it abstracts out several APIs providing support for:

* SQL
* MongoDB
* Cassandra
* Tables
* Gremlin

### Azure SQL Database

Definition: Relational DB based on the latest stable version of Microsoft SQL Server database.

Features:

* HA: 99.99%
* PaaS: Update, patching, backups, and monitoring are all managed
* Fully managed: No need to manage infrastructure or the OS
* Can process relational and non-relational data like graphs, JSON, and XML

**Key differences from SQL Managed Database**:

* Offers _less_ options that are available in Azure SQL Managed Database

See: https://docs.microsoft.com/en-us/azure/azure-sql/database/features-comparison

### Azure SQL Managed Instance

Definition:  Similar to SQL Database. Relational DB based on the latest stable version of Microsoft SQL Server database.

Features:

* HA: 99.99%
* PaaS: Update, patching, backups, and monitoring are all managed
* Fully managed: No need to manage infrastructure or the OS
* Can process relational and non-relational data like graphs, JSON, and XML
* Can use the Azure Database Migration Service (DMS) or native backup/restore

**Key differences from SQL Database**:
* Offers _more_ options that aren't available in Azure SQL Database
* Can manually initiate backups
* Has access to all built-in functions
* Collation choices at instance creation
* Cross-database name queries and transactions
* Database Mail

See: https://docs.microsoft.com/en-us/azure/azure-sql/database/features-comparison

### Azure Database for MySQL

Definition: Relational DB based on MySQL community edition

Features:

* HA at no additional cost
* Automatic backups + up to 35 days for a point-in-time restore
* Scale as needed within seconds
* Fully managed
* Several tiers offered

### Azure Database for PostgreSQL

Definition: Relational DB based on PostgreSQL database engine

Features:

* HA at no additional cost
* Automatic backups + up to 35 days for a point-in-time restore
* Scale as needed within seconds
* Fully managed
* SSL encryption between client and server communications

Available in two deployment options:

**Single Server**
* 3 tiers: Basic, General, and Memory Optimized
* Dynamic scaling

**Hyperscale (Citus)**
* Horizontally scalling using sharding
* Query parallelization across server for fast responses on large datasets
* Made for applications that need greater scale+performance for 100GB of data or more
* Supports multi-tenant, real-time analytics, high (transactional) throughput
* Standard connection + minimal changes

### Azure Synapse Analytics

Definition: Limitless analytics service for big data analytics.

Features:

* Serverless queries or provisioned resources at scale
* Unified experience to ingest+prepare+manage+serve data
* Data warehousing
* Big data analytics

### Azure HDInsight

Definition: Fully managed analytics service

Features:

* Works with Apache Spark, Apache Hadoop, Apache Kafka, Apache HBase, Apache Storm
* Supports Machine Learning Services
* ETL support
* Data Warehousing

### Azure Delta Lake Analytics

Definition: Simplified on-demand analytics job service for big-data

Features:

* Handle jobs of any scale
* Configure analytics power instantly
* Pay for when the job is running (cost effective)


### Azure Databricks

Definition: Apache Spark environment to build AI solutions and insights from data.

Features:

* Support for Python, Scala, Java, and SQL
* Support for data science frameworks like TensorFlow, PyTorch, and Scikit-Learn


## Azure identity, access, and security
LM: https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/


## Azure Active Directory (AAD)

Definition: Cloud-based identity and access management service

| Active Directory | Azure Active Directory |
| --                | --                     |
| Managed by your own org | Managed by Azure |
| On-premise identity control | Global identity control service|

**Note**: Can connect AAD with Active Directory for sign-in attempts

Features:

* Control access to applications and resources
* SSO functionality within apps, integration with existing creds
* Self-service password reset for users
* MSFT 365, Azure, and other services already use AAD

Services:

* Authentication
* Single Sign-On (SSO)
* Application management
* Device management (device registration)

Secure:

* Both internal and external resources
* Internal resources like on-premise (behind firewall) apps and resources


### Connect AD with AAD

* Azure AD Connect syncs user identities between on-premise and cloud (AAD).
* SSO, password resets, multi-factor auth within both systems

### Azure Active Directory Domain Services


Definition: Azure AD DS provides managed domain services like domain join, group policy, LDAP (Lightweight Directory Access Protocol), and Kerberos

* Create an Azure AD DS managed domain with a unique namespace
* Namespace becomes the domain name
* 2 Windows Server domain controllers are deployed into selected Azure region A.K.A replica sets.

DC stands for Domain Controllers

Features:

* No need to manage/configure DCs
* One-way synchronization from Azure AD to Azure AD DS (not backwards!)

### Single Sign-On

Definition: Allows to sign-in one time and use that credential for multiple applications and resources. Applications must trust the initial authenticator


### Multifactor Authentication

Definition: Prompts a user for an extra form (factor) of identification.

Feature: Prevents problems with compromised passwords

Uses two or more of:

* Something the user knows (a challenge question)
* Something the user has (phone)
* Something the user is (fingerprint)

### Azure AD Multi-factor authentication

Definition: Provides multifactor authentication capabilities on Azure Active Directory


### Passwordless Authentication

Definition: A way to authenticate without the need of passwords or extra security layers.

Example: A computer that is enrolled (registered) and Azure knows that it is associated with you.

Integrations:

* Windows Hello for Businness
* Microsoft Authenticator App
* FIDO2 security keys


### Windows Hello For Business

Definition: Uses biometric and PIN crednetials directly tied to the user's PC (only work on Windows PC) to access resources on-premises and in the cloud.

### Microsoft Authenticator App

Definition: A cellphone application that allows getting a notification that can enable a user to allow reousrces after using biometric information or PIN to confirm access.


### FIDO2 (Fast IDentity Online) Security Keys

Definition: It is an open standard for passwordless authentication alloing users to sign-in by using an external security key or platform key built into a device.

### Azure AD External Identities

Definition: A way to collaborate with partners (B2B) outside of your organization. External providers manage identity while AAD External Identities manages access.

Note: Sounds similar to SSO (Single Sign-On).

Features:

* B2B Collaboration: Let users choose their preferred identity to sing-in for your resources. B2B users are represented as guest users in your directory
* B2B Direct Connect: Two way trust with another Azure AD organization that enables external users.
* Azure AD Business to Customer (B2C): Publish applications (excluding Microsoft Apps) to consumers/costumers using B2C for identity and access management


### Azure Conditional Access

Definition: An Azure AD tool to allow/deny access to resources based on signals. Signals include who, where, and what device the user is requesting access from.

Use it when:

* Requiring Multifactor Authentication
* Requiring access to services through client applications
* Requiring access only through managed devices
* Blocking access from specific locations or devices

### Azure Role Based Access Control (RBAC)

Definition: A way to provide access based on role rules that apply to a group instead of per-user privileges. RBAC is applied to a scope which is one or more resource that the access applies to.


| -                | Reader | Resource-specific | Custom | Contributor | Owner |
| --               | -- | -- | -- | -- | -- |
| Management Group | Observers | <td colspan=3>Users managing resources</td> | Admins |
| Subscription     | Observers | <td colspan=3>Users managing resources</td> | Admins |
| Resource Group   | Observers | <td colspan=3>Users managing resources</td> | Admins |
| Resource         | <td colspan=5> Automated Processes</td> |


Azure RBAC uses an **allow model**. Roles providing permissions are _additive_ for resource and resource groups.

Note: Is enforced on any action that goes through Azure Resource Manager (Portal, Cloud Shell, Power Shell, and Azure CLI). It does *not enforce access permissions* at the application or data level.


### Zero Trust Model

Definition: A security model that assumes _the worst case scenario_. Verifies each request as it came from an uncontrolled network.

Principles:

* **Verify explicitly**:  Always authenticate/authorize based on all data points
* **Least Privilege Access**: Limit access with Just-In-Time and Just-Enough-Access.
* **Assume Breach**: Access segmentation, end-to-end encryption, analytics for visibility.

Classic Approach: System-wide access behind "secure" network
Zero Trust: All assets and resources are protected with central policy


### Defense In Depth

Definition: Protect information and prevent unauthorized access using mechanisms to slow down an attack.

Based on usage of layers of access. Each layer protects access further even if one layer is breached. These are:

* Physical (e.g. Hardware and datacenters)
* Identity: Use SSO, audit events, controlled access.
* Perimeter (e.g. DDoS): Firewalls and DDoS protection
* Network: Limit communication between resources. Deny everything by default.
* Compute: Secure access with patched systems (Malware, Viruses, Unpatched vulnerabilities)
* Application: Prevent and patch vulnerabilities. Secure design by default
* Data: Control access for confidentiality, integrity, and availability


### Microsoft Defender for Cloud
_ Assess, Secure, and Defend_
Definition: Monitors security and threat protection for cloud, on-premises, hybrid, and multicloud environments to provide guidance and notifiactions.

**Azure Native**

- **Azure PaaS**: Detects threats against services like App Service, SQL, and Storage Account.
- **Azure data services**: Helps classify data in SQL and get assesments across storage devices.
- **Networks**: Limit exposure to brute force attacks.

**Hybrid resources**
Customized threat intelligence for specific (custom) environments

**Multi-Cloud**
Includes protection on other clous like AWS and GCP, as well as:

- Assets and inventory
- Containers on EKS Linux Clusters
- Windows and Linux EC2 (AWS) Virtual Machines

Three vital needs:

1. Continously Assess: Identify and automatically track vulnerabilities for VMs, Container Registies, and SQL Servers.
1. Secure (harden resources): Provides constant monitoring and recommendations to reduce attacks with secure configuration standards across resources.
1. Defend (detect and resolve threats): Security alerts and advanced threat protection features.

Security alerts generate:

- Description of the affected resources
- Suggests remediation steps
- Optionally a logic app trigger in reponse
