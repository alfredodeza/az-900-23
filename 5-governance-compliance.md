# Identity, Governance, Privacy, and compliance

LP: https://docs.microsoft.com/en-us/learn/paths/az-900-describe-identity-governance-privacy-compliance-features/


# Identity 

## Authentication and Authorization

**Authentication**

* Establishes identity for access
* Challenges a party for legitimate credentials
* Establishes whether the user is who they say they are


**Authorization**

* Establishes the **level** of access for authenticated user
* Specifies what data a user is allowed to access and what they can do with that data


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

## Azure AD Multi-factor Authentication

Definition: Service that provides multifactor authentication capabilities.

### Multifactor Authentication

Definition: user is prompted during sign-in for additional forms of identification

Requires two or more elements to authenticate:

* Something the user knows (e.g. an email)
* Something the user has (e.g. a phone)
* Something the user is (e.g. fingerprint or face scan)

### Conditional Access

Definition: A tool that AAD uses to allow/deny resources based on identity _signals_

**identity signals**: Who the user is, where the user is, what device the user is requesting access from.

Provides granular multifactor authentication.

Available to AAD Premium

# Governance

## RBAC

Definition: Role based access control based on an allow model. Access that applies to a scope which is a resource or set of resources.

Scopes:

* Management group
* Single subscription
* Resource group
* Single resource

| Role name | Scope     | Permissions |
| --         | --        | --        |
| Owner        | Management Group | Can manage everything in all subscriptions |
| Reader     | Subscription Group | View every resource group within the subscription |
| Contributor | Resource Group |  Can manage resources of all types within the resource group, but not other resource groups|

Permissions are compounded: one app gives you read, another gives you write, means read+write permissions

**Enforcement**: Goes through Azure Resource manager (access via Portal)

Apply it to:

* Individuals
* Groups
* Service principals or other managed identities

**Management**: Through IAM (Acccess Control)

## Resource Locks

Definition: Prevents resources from being accidentally deleted or changed

| Level        | Permissions        |
| --         | --                 |
| CanNotDelete | Authorized users can still read and modify but can't delete |
| ReadOnly | Authorized users can read but cannot change. Like Reader role in RBAC |

**Changes to locked resource**: Must remove the lock first. Regardless of RBAC permissions.

**Combine**: Use locks with Azure Blueprints to prevent accidental lock removal. Blueprints can automatically
replace the resource lock if removed.

## Tags

Definition: provides extra information about resources.

Useful for:

* Resource management
* Cost management
* Operations management
* Security
* Governance and compliance
* Workloads and optimization

Add tags with: 
* PowerShell + CLI
* ARM templates (Azure Resource Manager)
* REST API
* Azure Portal

**Azure Policy** Allows tag management. Tags for a resource group aren't auto applied to resources within the group. Azure Policy can make resource inherit tags or enforce tag conventions

## Azure Policy

Definition: Enables you to create, assign, and manage policies that control resources. Highlights non-compliant resources and prevents noncompliant resources from being created.

Can automatically remediate noncompliant resources+configurations

Works with Azure DevOps for CI and Pipeline for app pre and post deployment phases.

**Initiative**: Individual or group of related policies.

Built-in initiatives for: 

* Storage
* Network 
* Compute 
* Security Center
* Monitoring

Enable it by: 

1. Create a definition
1. Assign definition to resources
1. Review results

Enforce:

* VM SKUs
* Allowed geographical locations
* Multifactor authentication with specific permissions
* CORS. Only required domains can interact with certain apps
* Install system updates on machines

Policy assignment:

* To resources
* Takes place within a scope (management group, single subscription, or resource group)
* Automatically inherited for all child resources within a resource group (can be excluded)

Review:

* Each resource is marked as compliant or noncompliant
* Evaluation happens every hour

### Initiatives

Definition: groups related policies. Helps track for a larger objective

Initiatives are assigned to a scope of a mangement group, subscription, or resource group.

## Azure Blueprints

Definition: Orchestrate/automate deployment of resource templates and artifacts like Roles, Policies, ARM templates, and Resource groups

| Action        | Description        |
| --            | --                |
| Define/Create | Describes what should be deployed |
| Assign         | An actual deployed resource |
| Track         | Capture changes via versioning |

**Artifacts**: a component in a Blueprint definition. Can contain zero or more parameters to configure 


## Cloud Adoption Framework (CAF)

Definition: Provides guidance for cloud adoption 

1. Create a strategy
1. Plan 
1. Ready for cloud adoption
1. Adopt the cloud
1. Govern and manage

## Subscription governance strategy

**Billing** One report per subscription. When creating subscription take into account internal billing requirements

**Access Control** A subscription is a boundary for Azure resources. Each subscription is mapped to an AAD tenant. Each tenant can set granular access via RBAC

**Limits** Subscriptions have resource limitations. Exceeding limits means more subscriptions. A management group can help with subscriptions.


## Compliance

Microsoft services build on several regulatory compliance controls. Grouped by:

* Global
* US Government
* Industry
* Regional

### Criminal Justice Information Service (CJIS)

Azure is the only major cloud that contractually commits to CJIS security policy - just like law enforcement

### Cloud Security Alliance STAR Certification

Azure, Intune, Power BI are CSA STAR certified. 

**CCM**: Cloud Controls Matrix.

This certification means that:

* Service conforms to applicable requirements
* Has addressed issues critical to cloud security
* Asses against the STAR capability maturity model in CCM areas

### European Union Model Clauses

Azure offers EU customers contractual guarantees around transfers of personal data outside of the EU.

### Health Insurance Portability and Accountability Act (HIPAA)

Azure offers HIPAA business associate agreement (BAA) to adhere to security+privacy provisions.

### International Organization of Standards/International Electrotechnical Commission 27018 

Microsoft has adopted ISO/IEC 27018 code of practice for processing information by cloud service providers.

### Multi-tier Cloud Security Singapore

Microsoft is certified all classifications:

* IaaS
* PaaS
* SaaS

### Service Organization Controls 1,2, and 3

Microsoft is audited annually against the SOC report framework. Covering security, availability, and integrity.


### National Institute of Standards and Technology Cybersecurity Framework (NIST) (CSF)

A voluntary framework that consists of standards, guidelines, and best-practices to manage cybersecurity threats

Microsoft has undergone several audits and Office 365 is certified to the objectives in NIST CSF

## Privacy, Online Services, and Data Protection

### Privacy Statement

Explains personal data that Microsoft collects and how it is used and for what purpose.


### Online Services Terms

OST is a legal agreement between Microsoft and the customer for the processing and security of customer+personal data. You must license
through a subscription.


### Data Protection Addendum (DPA)

Details the data processing and security terms for online services:

* Law compliant
* Processed data disclosure
* Data security
* Data transfer, retention, and deletion

### Trust Center

Definition: Service that provides information about security, privacy, and compliance offerings (e.g. ISO certs) across products.


### Azure Government

Definition: A separate instance of Azure in physically isolated datacenters and networks located in the US. Addresses security+compliance needs of US Federal agencies. 

Available in 8 geographies with the boradest compliance and Level 5 DoD approval.


### Azure China 21Vianet

Definition: A physically separated instance of cloud services in China operated by 21Vianet.