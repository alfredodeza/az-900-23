# Identity, Governance, Privacy, and compliance features

LP https://docs.microsoft.com/en-us/learn/paths/az-900-describe-general-security-network-security-features/

## Core Azure Identity Services

### Azure Security Center

Definition: a monitoring service for security across all services in Azure and on-premises

* Monitors across on-premises and cloud workloads
* Applies security settings
* Provides security recommendations
* Continuously monitors, automatic identification of vulnerabilities
* Allows defining rules for allowing applications to run
* Detects and analyses attacks, investigates threats
* Provides just-in-time access network control
* Views _overall_ regulatory compliance - Assigns a Secure score

Threat protection:
* Just-in-time VM Access
* Checks unauthorized applications running on VMs
* Monitor internet traffic patterns of VMs
* File integrity monitoring

**Secure Score**

Definition: Is a measurement of an organization's percentage of satisfied security recommendations

* Based on security controls or groups of security recommendations



### Azure Sentinel

Definition: is a cloud-based Security Information and Event Management System (SIEM)

* Collects cloud data across all devices, users, apps, infrastructure for on-premise and multiple-clouds
* Inteligent threat detection (past and present) - uses AI for suspicious activities and investigation
* Orchestrate and automate common tasks (**Azure monitor workbooks**)

### Azure Key Vault

Definition: centralized cloud service for storing app secrets. Store them in Hardware Security Modules (HSMs)

Manage:
* secrets
* encryption keys
* SSL/TLS certificates

Benefits:

* Centralized app secrets
* Access monitoring and control
* Integrates with Azure services 

### Dedicated Host

Definition: Provides a dedicated physical server to host VMs (Windows+Linux)

* Exclusive control of the underlying physical host for VMs
* Helps with compliance requirements for isolated servers
* Pick and choose processor/VM series/sizes on the same host
* HA: provision multiple hosts in a host group
* Optional maintenance control for when maintenance updates happen
* Pricing is per dedicated host, regardless of VMs hosted


### Defense in Depth

Definition: protect information using a layered strategy with data secured at the center.

* **Security Posture**: Confidentiality, Integrity, Availability _CIA_
* **confidentiality**: restrict access, least privilege
* **integrity**: prevent unauthorized changes to information
* **availability**: access only for authorized users

### Azure Firewall

Definition: managed cloud-based network security service for Azure virtual networks

* High Availability + scalability
* Inbound and outbound filtering rules
* Azure Monitor logging
* Inbound Destination Network Address Translation (DNAT)

You can configure:

* Application rules for FQDNs
* Network rule for source, protocol, and destination port and address
* NAT rules

Note: Azure Application Gateway provides Web Application Firewall (WAF) which is also a firewall.

### Azure DDoS Protection

Definition helps protect your resources from DDoS attacks

* **Basic**: Enabled by default, for free as part of Azure subscription. Always on monitoring. Helps mitigate
attacks across regions.
* **Standard**: Additional mitigation capabilities for Azure Virtual Networks. Easy to enable, no app changtes needed.
Policies are applied to public IPs. 

Prevents the following attacks:

* **Volumetric**: Floods the network layer with legitimate-looking traffic
* **Protocol**: Makes a target inaccessible by exploiting layer 3 and layer 4 protocols
* **Resource-layer**: Targets web app packets to disrupt data transmission between hosts.

### Network Security Groups (NSGs)

Definition: Enables you to filter traffic to/from Azure resources within a virtual network (like an internal firewall)

* NSG can have many rules within an Azure subscription. 
* A new rule has default rules to provide a security baseline 
* Can't remove default rules, but you can override them

### Network security strategy/solution

* Secure the perimeter (Firewall, DDoS)
* Secure the network layer (restrict connectivity, limit communication) (NSGs)
* Combine services: NSG + Firewall + DDoS, WAF, etc...