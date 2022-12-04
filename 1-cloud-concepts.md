# Describe Cloud Concepts

LP: https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/

Identify Cloud Computing benefits, use GASHED:

* Geo-distribution
* Agility
* Scalability
* High Availability
* Elasticity
* Disaster Recovery


## Azure Portal

Definition: Web-based unified console that allows you to build, manage, and monitor everything in Azure.

## Azure Marketplace

Definition: Connects users to partners and vendors that offer solutions/services for Azure

## Accounts

Azure Account -> Many subscriptions -> Many Resource groups -> Resources

## Types of Cloud

| Type | Description | Expenditure |
| --   | --          | -- | 
| Public | Services over the internet. Owned by a third party| OpEx |
| Private | Exclusive by users from a company. Can be on-premise, datacenter, or hosted by a third-party service provider.| CapEx |
| Hybrid | Combination of Public and Private| |

## Expenses

Describe CapEx (Capital Expenditures) and OpEx (Operational Expenditures)

| Type | Description |
| -- | -- |
| Capital Expenditure (CapEx) | Up-front spending on infrastructure. Value is reduced over time | 
| Operational Expenditure (OpEx) | No up-front cost. Spending only on services and billed for what you use | 

## Consumption-Based Model

Is the basis of OpEx: 

* No up-front costs
* Only pay for what you use/need
* Pay for additional resources when they are needed
* Stop paying for what you don't use


## Cloud Service models


| Model | Description | Complexity/Ownership |
| -- | -- | -- | 
| IaaS | OS and Network owned by the user, including maintenance and configuration | High | 
| PaaS | Apps are deployed into a managed OS. No ownership of hardware or software requirements | Medium |
| SaaS | User only provides data. Everything else is managed. E.g. MS Office | Low |

## Subscriptions, Management Groups, and Resources

| Name | Definition | 
| -- | -- |
|Management Groups|Manage access, policy, compliance for multiple subscriptions|
|Subscriptions|Groups accounts with resources. Can be used to manage costs+resources|
|Resource Groups| A logical grouping of services (resources)|
|Resources| Services that you create. E.g. a Virtual Machine|

## Azure Regions

Definition: A geographical area with one or more datacenters nearby and networked together.

**Special Regions**: US DoD, US Gov: physically+logically isolated with additional compliance certifications. China 
is operated by 21Vianet.


## Azure availability Zones

Definition: One or more physically separate datacenters within an Azure region. A.K.A. Isolation Boundary (HA/redundancy).

Availability Zones are interconnected with ultra high-speed, private, fiber network.

Not all regions have AZs.

Services that support AZs have these categories:

* **Zonal service**: Pins to a zone
* **Zone-redundant**: Auto-replication across zones
* **Non-regional**: HA in an Azure geography. 

## Azure Region Pairs

Definition: Each Azure region is **always paired** with another region within the same geography.

AZs have one or more datacenters, and a Region has at least 3 zones. 

Helps protect against natural disasters or civil unrest. Separated at least 300 miles.

Replication resides always within the same Geography as the pair except for Brazil South.

## Azure resources and Azure resource Manager

**Resource**: A manageable item within Azure. Like a database or a VM
**Resource group**: A grouping of resources you want to manage as a group.

### Azure Resource Groups

Can contain anything you create in Azure to form a logical grouping of services (resources). Helps provide organization.

* **Life cycle**: If you delete a resource group, all contained resources are deleted as well. Makes it easier to get rid of.
* **Authorization**: A resource group is a scope for applying RBAC

### Azure Resource Manager

Definition: Deployment and management service for Azure. CRUD for Azure resources

* Manage infrastructure with templates
* Deploy, manage, and monitor
* Define dependencies between resources for correct ordering
* Apply RBAC and tags

## Azure subscriptions

Definition: Provides you with authenticated and authorized access to products and services. Always linked back to an account.

An account can have one or many subscriptions.

Types of subscription boundaries:

* **Billing boundary**: Determines how an Azure account is billed. You can create multiple subscriptions for different billing requirements.
* **Access Control boundary**: Access-management policies happen at the subscription level. You can control access+resources for specific subscriptions.

Additional subscription helps with:

* **Environments**: Separate environments via subscriptions. E.g. development and testing
* **Org structure**: Marketing and IT, helping manage access and limit resources
* **Billing**: Make it easier to track billing better.

## Azure management groups

Definition: Provides a level of scope above subscriptions. Helps organize subscriptions into groups.

Helps provide user access to multiple subscriptions with a single RBAC that gets inherited
