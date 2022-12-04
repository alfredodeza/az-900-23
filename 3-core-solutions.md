LP: https://docs.microsoft.com/en-us/learn/paths/az-900-describe-core-solutions-management-tools-azure/

find about days and hours of sla

## Azure IoT fundamentals

LM https://docs.microsoft.com/en-us/learn/modules/iot-fundamentals/

### Azure IoT Hub

Definition: Managed service hosted in the cloud. Central hub for bi-directional communication with devices and the cloud.

Features:

* Device-to-cloud telemetry
* File upload from devices
* Control devices from the cloud
* Monitoring of device creation, failures, connections

Key difference with IoT Central: More control, less managed (no dashboard). Telemetry analysis.

### Azure IoT Central

Definition: Builds on IoT Hub with a dashboard to connect, monitor and manage IoT Devices

Features:

* Dashboard for managing devices
* Push firmware updates to devices
* Provides starter templates for common scenarios

Key difference with IoT Central: Less control, more managed (dashboard included).

### Azure Sphere

Definition: End-to-end, secure IoT solution. From hardware to OS and messaging from the device to the message hub.

Three parts:

1. **Azure Sphere Micro-Controller (MCU)**: Processes OS and signals from attached sensors.
1. **Custom Linux OS** that handles communication with the security service
1. **Azure Sphere Security Service (AS3)**: Makes sure the device hasn't been compromised

Features:

* Built-in communication and security features for IoT devices

## Azure AI Fundamentals

LM https://docs.microsoft.com/en-us/learn/modules/ai-machine-learning-fundamentals/

### Azure Machine Learning

Definition: Platform for working with models. Tools and services that allow you to connect to data, train, and deploy models.

Features:

* Define how to obtain, handle, and split data in training and test sets.
* Train and evaluate modules with programming languages like Python
* Pipeline creation for compute-intensive tasks
* Best-algorithm deployment with an API to a REST endpoint

### Azure Cognitive Services

Definition: Provides pre-built ML models to see, hear, speak, understand and reasoning.

Features:

* Solves generic problems, like text sentiment analysis, image or face recognition

4 categories:

1. Language: Process NLP
1. Speech: Speech-to-text, and text into natural sounding speech. Language translations
1. Vision: Analyze and recognize pictures, videos or other visual content
1. Decision: Automatic and Personalized recommendations for users. Detect abnormalities in Time Series data.

### Azure Bot Service and Bot Framework

Definition: Platform for creating virtual agents that can reply to questions as a human.

Features:

* Virtual agent that can communicate intelligently with humans
* Uses other Azure services like Azure Cognitive Services to proces information better

## Serverless Fundamentals

LM https://docs.microsoft.com/en-us/learn/modules/serverless-fundamentals/

### Azure Functions

Definition: Use a programming language that responds to an event based on a queue, timer, or HTTP request.

Features:

* Use common languages like C#, Python, JavaScript, Typescript, Java and PowerShell
* Scales automatically
* Stateless environment, but can be connected to storage to persist data
* Orchestration possible with Durable functions, chaining functions together and maintaining state.

Key difference from Azure Logic Apps: Azure is a serverless compute service, not meant to be a long-running business-logic process that connects with other services.

### Azure Logic Apps

Definition: A low-code/no-code platofrm that helps automate and orchestrate tasks, business processes and workflows.

Features:

* Integration for apps, data, system, enterprise (EAI), and B2B
* Web-based designer triggered from Azure services
* Trigger from events like timers, a queue, or an HTTP request (like functions)
* Over 200 pre-made solutions (connectors) for SalesForce, SAP, Oracle DB, and file shares

Key difference from Azure Functions: Logic Apps is an _orchestration service_. Pricing is dependent on the connector.

## Azure DevOps & DevTest Labs

LM https://docs.microsoft.com/en-us/learn/modules/azure-devops-devtest-labs/

### Azure DevOps

Definition: Suite of services for all stages of software development lifecycle

Services included:

* Azure Repos: Source-code repositories
* Azure Boards: Project management
* Azure Pipelines: CI/CD automation tooling
* Azure Artifacts: A repository for hosting artifacts that can be used in deployment or testing pipelines
* Azure Test Plans: Automated testing tool for CI/CD pipelines that can ensure quality before a release

Key difference from GitHub: Enterprise development, with more project-management, planning tools and fine-grained access control.

### GitHib and GitHub Actions

Definition: Git Source-code repositories and CI/CD automation

Features:

* Shared repos that allow code reviews, comments, questions, and discussions before merging code
* Helps project management with Kanban boards included
* Issue reports, discussion, and tracking
* CI/CD pipelines via GitHub Actions
* Wiki for collaborative docs
* SaaS or on-premise capabilities

Key difference from Azure DevOps: More lightweight, less customizable, less project-management and planning tools.

### Azure DevTest Labs

Definition: Service for automating building, setup, and tearing down of VMs that build software projects.

Features:

* Test across a variety of environments and builds
* Support for anything that ARM templates can deploy
* Shutdown or fully deprovision VMs after completion

## Management Fundamentals

LM https://docs.microsoft.com/en-us/learn/modules/management-fundamentals/2-identify-product-options

### Azure Portal

Definition: Web-based UI to access almost every feature and service of Azure.

Features:

* View all services you are using
* Create new services
* Configure new or existing services
* View reports

### Azure Mobile App

Definition: iOS and Android mobile app to access Azure resources remotely.

Features:

* Monitor health and status of services
* Check alerts
* Restart web apps or VMs
* Run the CLI or PowerShell commands to manage Azure resources


### Azure PowerShell

Definition: A shell where you can execute commands called _cmdlets_ (command-lets) that call into the Azure REST API for resource/service management.

Features:

* Execute independently or combined to orchestrate setup, teardown, or maintenance or 1 or more resources
* Deploy an entire infrastructure wich might contain hundreds of resources
* Use imperative code
* Create repeatable+automatable processes by using code
* Windows, Linux, OSX, and browser availability via Azure Cloud Shell

### Azure CLI

Definitio: A CLI tool to execute commands in Bash that call the Azure REST API for resource/service management.

It is almost **the same** as Azure PowerShell

Key difference: The syntax used. If you are proficient in Bash, then use the Azure CLI.

Features:

* Execute independently or combined to orchestrate setup, teardown, or maintenance or 1 or more resources
* Deploy an entire infrastructure wich might contain hundreds of resources
* Use imperative code
* Create repeatable+automatable processes by using code
* Windows, Linux, OSX, and browser availability via Azure Cloud Shell

### ARM Templates

Definition: Describe infrastructure in a declarative way using JSON.

Features:

* ARM templates are verified before execution
* Orchestration of resources in parallel
* Define only the desired state and configuration of each resource
* Templates can use PowerSHell or the Azure CLI for before/after actions

## Monitoring Fundamentals

LM https://docs.microsoft.com/en-us/learn/modules/monitoring-fundamentals/

### Azure Advisor

Definition: Evaluates your Azure resources and makes recommendations for reliability, security, performance, and reduce costs.

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

### Azure Monitor

Definition: Platform to collect, analyze, visualize, and take action based on data from your entire Azure **and on-premise environment**

Features:

* Monitor applications, integrating them with PagerDuty, Jira, or Azure DevOps
* Monitor and optimize your infrastructure, including VMs, K8s, and Storage
* Monitor and diagnose your network, trigger packet capture or analyze routing issues
* Supports an extensive query language to analyze and get insights from operational data
* Visualize, analyze, gain insights, and set alerts based on monitoring data

Application Insights uses Azure Monitor under the hood

### Azure Service Health

Definition: A personalized view of Azure services, regions, and resources health.

status.azure.com does **not** provide the full picture. as its main informational dashabord

Features:

* Both major and smaller health displays, localized to issues that affect you
* Peronalizable to services and regions that are interesting to you
* Set up alerts to help triage outages
* Provides official incident reports and Root Cause Analyses (RCAs)
* Advertises **Planned Maintenance** that can affect availability
* Publishes **Health Advisories** that include service retirements (sunsetting) or breaking changes.

Key difference with status.azure.com: The status dashboard is **not** personalized and not granular to issues that might affect you directly.
