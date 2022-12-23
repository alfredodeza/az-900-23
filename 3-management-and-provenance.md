# Azure Management and Governance

[Learning Path](https://learn.microsoft.com/training/paths/describe-azure-management-governance/?WT.mc_id=academic-0000-alfredodeza)

## Cost management

[Learning Module](https://learn.microsoft.com/training/modules/describe-cost-management-azure/?WT.mc_id=academic-0000-alfredodeza)

| Service | Definition |
| -- | --|
|**Azure Cost management + Billing**| A Free service that helps you grasp your Azure bill, manage subscription, monitor, optimize and control spending.|
|**Azure Reservations** | Offers discounted pricing on certain Azure services for reserving and paying in advance for services|
|**Azure Pricing Calculator**| A calculator that estimates cost based on all preceding factors according to specific requirements|
|**Azure Advisor** |Identifies unused/underutilized resources and makes recommendations.|
|**TCO Calculator** | Helps estimate the cost savings of operating your solution on Azure over time vs. on-premise datacenter |

## Azure Pricing Calculator

Definition: A calculator that estimates cost based on all preceding factors according to specific requirements

## Azure Advisor

Definition: Identifies unused/underutilized resources and makes recommendations.

## Spending limits

Prevent accidental overrun by setting limits.

## Azure Reservations

Definition: offers discounted pricing on certain Azure services for reserving and paying in advance for services

## Azure Cost Management + Billing

Definition: A Free service that helps you grasp your Azure bill, manage subscription, monitor, optimize and control spending.

## Features and tools for Governance and Compliance

[Learning Module](https://learn.microsoft.com/training/modules/describe-features-tools-azure-for-governance-compliance/?WT.mc_id=academic-0000-alfredodeza)

### Azure Policy

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

### Azure Blueprints

Definition: Orchestrate/automate deployment of resource templates and artifacts like Roles, Policies, ARM templates, and Resource groups

| Action        | Description        |
| --            | --                |
| Define/Create | Describes what should be deployed |
| Assign         | An actual deployed resource |
| Track         | Capture changes via versioning |

**Artifacts**: a component in a Blueprint definition. Can contain zero or more parameters to configure


### Resource Locks

Definition: Prevents resources from being accidentally deleted or changed

| Level        | Permissions        |
| --         | --                 |
| CanNotDelete | Authorized users can still read and modify but can't delete |
| ReadOnly | Authorized users can read but cannot change. Like Reader role in RBAC |

**Changes to locked resource**: Must remove the lock first. Regardless of RBAC permissions.

**Combine**: Use locks with Azure Blueprints to prevent accidental lock removal. Blueprints can automatically
replace the resource lock if removed.


### Service Trust Portal

Definition: Centralized location for content, tooling, and resources for compliance and privacy for Azure.

Example: Applying GDPR constraints or enabling tooling to comply with GDPR in Azure.

## Features and tools  for managing and deploying Azure resources

[Learning Module](https://learn.microsoft.com/training/modules/describe-features-tools-manage-deploy-azure-resources/?WT.mc_id=academic-0000-alfredodeza)

### Azure Portal

Definition: Build, manage, and organize custom view using the web UI in one centralized place

### Azure CLI

Definition: A CLI tool to execute commands in Bash that call the Azure REST API for resource/service management.

It is almost **the same** as Azure PowerShell

Key difference: The syntax used. If you are proficient in Bash, then use the Azure CLI.

Features:

* Execute independently or combined to orchestrate setup, teardown, or maintenance or 1 or more resources
* Deploy an entire infrastructure wich might contain hundreds of resources
* Use imperative code
* Create repeatable+automatable processes by using code
* Windows, Linux, OSX, and browser availability via Azure Cloud Shell

### Azure Cloud Shell

Definition: Cloud service that integrates fully with the Azure CLI and the PowerShell

### Azure PowerShell

Definition: A shell where you can execute commands called _cmdlets_ (command-lets) that call into the Azure REST API for resource/service management.

Features:

* Execute independently or combined to orchestrate setup, teardown, or maintenance or 1 or more resources
* Deploy an entire infrastructure wich might contain hundreds of resources
* Use imperative code
* Create repeatable+automatable processes by using code
* Windows, Linux, OSX, and browser availability via Azure Cloud Shell

### Azure Arc

Definition: Allows you to manage both Azure and non-azure resources with ARM (Azure Resource Manager)

Works for servers, K8s, Azure Data services, SQL Server, and VMs (preview)


### Azure Resource Manager and ARM Templates

Definition: Deployment and management service for Azure. Abstracts management for CRUD operations in services and infrastructure.

Benefits:

* Manage infrastructure through templates instead of scripts (ARM templates)
* Deploy and re-deploy solutions to a consistent state
* Define or update dependencies in a specific order
* Apply tags for logical organization of resources
* Native RBAC integration

Templates allow you to:

* Create declarative syntax (defining what you want, not the programming logic)
* Repeatable results
* Orchestration (ordering of operations)
* Modular files (smaller reusable files)
* Extensible via PowerShell or Bash

ARM Template features:

* ARM templates are verified before execution
* Orchestration of resources in parallel
* Define only the desired state and configuration of each resource
* Templates can use PowerSHell or the Azure CLI for before/after actions


## Monitoring tools in Azure

[Learning Module](https://learn.microsoft.com/training/modules/describe-monitoring-tools-azure/?WT.mc_id=academic-0000-alfredodeza)


### Azure Advisor

Definition: Evaluates and then provides recommendations for five categories: reliability, security, performance, operational excellence, and reduce costs.

Uses a dashboard with the 5 categories to visualize its recommendations.

Features:

* Get alerts on new recommendations that you can use, dismiss, or postpone
* Personalized recommendations for _all your subscriptions_
* Available in the Azure Portal and the REST API

5 categories:

* **Reliability**: Improve availability of applications
* **Security**: Detect threats and vulnerabilities
* **Performance**: Improve speed of applications
* **Cost**: Optimize/reduce Azure spending
* **Operational Excellence**: Deployment best-practices, efficiency workflow, resource management


### Azure Service Health

Definition: Tracks the status of **both** the Azure overall status as well as your individual resources

| Type | Description |
| -    | -           |
| Azure Status    | Overall Azure status, globally. Includes service outages. |
| Service Health  | Narrower view of Azre services and regions |
| Resource Health | Custom view of _your_ individual resources with historical data |

status.azure.com does **not** provide the full picture. as its main informational dashabord

Features:

* Both major and smaller health displays, localized to issues that affect you
* Peronalizable to services and regions that are interesting to you
* Set up alerts to help triage outages
* Provides official incident reports and Root Cause Analyses (RCAs)
* Advertises **Planned Maintenance** that can affect availability
* Publishes **Health Advisories** that include service retirements (sunsetting) or breaking changes.

**Key difference** with status.azure.com: The status dashboard is **not** personalized and not granular to issues that might affect you directly.


### Azure Monitor

Definition: Platform to collect, analyze, visualize, and take action based on data from your entire Azure **and on-premise environment**

Features:

* Monitor applications, integrating them with PagerDuty, Jira, or Azure DevOps
* Monitor and optimize your infrastructure, including VMs, K8s, and Storage
* Monitor and diagnose your network, trigger packet capture or analyze routing issues
* Supports an extensive query language to analyze and get insights from operational data
* Visualize, analyze, gain insights, and set alerts based on monitoring data

Application Insights uses Azure Monitor under the hood

