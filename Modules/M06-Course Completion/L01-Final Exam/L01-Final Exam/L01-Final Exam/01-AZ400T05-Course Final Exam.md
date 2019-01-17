##Checkbox##

<<display_name:AZ400T05_CB_1; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following describes *Infrastructure as Code* (IaC) correctly?<<

(choose two)

[x] IaC involves using preset definitions for initializing machines and setting up environments.
[ ] IaC impedes Traceability.
[ ] IaC is used to manually deploy Azure resources.
[x] IaC provides greater consistency across multiple environments.

[explanation]
IaC involves using preset definitions for initializing machines and setting up environments, and IaC provides greater consistency across multiple environments, are the correct answers.

IaC impedes Traceability is incorrect, because IaC actually facilitates Traceability by making it easier to trace what was deployed, when, and how.
IaC is used to manually deploy Azure resources is also incorrect because implementing IaC helps to automate the deployment process.

With IaC, you capture your environments in a text file (script or definition), including any networks, servers, and other compute resources. The script or definition file can be checked into version control, and used as the base source for updating existing environments or creating new ones. By using consistent definitions, IaC can reduce the possibility of introducing human error when initializing resources and can help to maintain consistency across multiple environments.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_2; max_attempts:1; showanswer:never; weight:1>>

>>True or false: The declarative approach is more generally preferred to the imperative approach, for implementing Configuration as Code?<<

(x) True
( ) False

[explanation]
True: The declarative approach *is* more generally preferred to the imperative approach, for implementing Configuration as Code.

The *Declarative* (functional) approach is used to state 'what' the final state should be. When the script or definition is run, the machine is initialized or configured to achieve the declared finished state. However, the declarative approach does not define 'how' the final state should be achieved.

Alternatively, with the *Imperative* (procedural) approach, a script or definition file states 'how' a machine's final state is to be achieved. When the file is run, the steps required to get to the finished state are executed. The imperative approach defines what the final machine state should be, but also specifies how that final state is to be achieved.

The declarative approach abstracts away the methodology for how a final state is to be achieved. As a result, a declarative script or definition file can be easier to read and understand. This also makes declarative outcomes easier to write and define. Specifying the desired final state, without providing code to achieve that state, makes the declarative approach less restrictive and open to optimization. These are the reasons why the declarative approach is more generally preferred to the imperative approach.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_3; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following defines *idempotency* correctly, in the context of Infrastructure and Configuration as Code?<<

(x) Idempotency is the application of one or more operations, against a resource, which result in the same outcome, after each operation.
( ) Idempotency is the application of one or more operations, which result in different outcomes, after each operation.
( ) Idempotency is the application of one or more operations, which result in unpredictable outcomes, after each operation.
( ) Idempotency is the application of one or more operations, which result in a unique outcome, after each operation.

[explanation]
Idempotency is the application of one or more operations, against a resource, which result in the same outcome, after each operation, is the correct answer.

All other answers are incorrect, as they are slight contradictions of the correct answer.

With idempotency, using a script or template to apply a deployment to a set of resources, innumerable times, should always produce the same result, after each application of the script or template. With Infrastructure and Configuration as Code, it is best practice to consider *idempotency* whenever you create scripts and templates. Idempotency considerations are especially relevant to cloud services. Ignoring *idempotency* is considered bad practice.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_4; max_attempts:1; showanswer:never; weight:1>>

>>A build up of development work, due to non-optimal code implementations, which need to be completed at a future time, is an example of what?<<

( ) Technical Slack
( ) Technical Debt
(x) Technical Depth
( ) Technical Waste

[explanation]
Technical Depth is the correct answer.

All other answers are incorrect, as these terms are not used to describe a build up of development work in the context of software development.

In software development, release schedules are often prioritized. As a result, development projects include provisions for revisiting any non-optimal implementations. For example, development teams may need to postpone fixing non-critical bugs, or skip meeting localization and accessibility criteria, until the end of a release cycle. As this pattern emerges, teams inevitably begin building up outstanding work, called *Technical Debt*, which will need to be completed at a future time (i.e. like a debt that needs to be paid back). Accruing too much technical debt can undermine productivity by creating unforeseen workloads that will eventually impede progress. Without proper planning and management, technical debt can place huge demands on an organization’s resources which may subsequently cause problems for the organization.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_5; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following is the correct term for the process that affects changes in the state of a set of resources, from the state in which they were originally deployed?<<

( ) Configuration Shift
( ) Configuration Spread
( ) Configuration Bias
(X) Configuration Drift

[explanation]
Configuration Drift is the correct answer.

All other answers are incorrect, as these are not terms for the process affecting changes in the state of a set of resources that are used in the context of software development.

The process that affects changes in the state of a set of resources, from the state in which they were originally deployed, is called *Configuration Drift*. Configuration Drift results from changes made by people, processes or programs, and it can occur from manual intervention or from automation. The ongoing administration and maintenance of infrastructure invariably involves adapting configurations. Over time, the changes made to the configurations of environments and resources may lead to issues, as legacy changes can be hard to trace and are often prone to human error. The more an environment drifts from its original state, i.e. Configuration Drift, the more likely it is for an application to encounter issues. The greater the degree of Configuration Drift, the longer it can take to troubleshoot and rectify issues.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_6; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence correctly. An Azure Resource Manager Template is… ?<<

(choose two)

[x] a precise definition of all the Azure Resource Manager resources within a deployment.
[ ] a group of VM instances created in a single operation.
[x] written in JSON.
[ ] a set of tools for Azure subscriptions.

[explanation]
An Azure Resource Manager Template is a precise definition of all the Azure Resource Manager resources within a deployment, and written in JSON, are the correct answers.

All other answers are incorrect.

An Azure Resource Manager Template is a precise definition of all the Azure Resource Manager resources within a deployment. You can deploy an Azure Resource Manager Template into a resource group in a single operation. Resource Manager Templates are declarative and are written in the JavaScript Object Notation (JSON) format. By using a template, you can deploy and redeploy the resources within your solution as often as you need to, across your development, test and production environments. Using templates ensures that the deployment state of your resources remains consistent, each time you deploy them. It is possible to create your own template, but it is easier to use an existing template and customize it to your specific needs.
[explanation]

----
##Dropdown##

<<display_name:AZ400T05_DD_7; max_attempts:1; showanswer:never; weight:1>>

>>Certain combinations of resources sometimes need to be provisioned in a particular order. Which of the following keys is used to define these relationships within a template?<<

[[
type key
(dependsOn key)
location key
name key
]]

[explanation]
The dependsOn key is the correct answer.

All other answers are incorrect because these keys are not used to define relationships within a template. The type key is used to define the resource type, the name key defines name of a resource and the location key defines the location of a resources (in the form of a URI).

Certain combinations of resources sometimes need to be provisioned in a particular order. For example, it makes sense to create a SQL server before initializing a SQL database. In this relationship, the SQL database resource is *dependent* upon the SQL server resource. Within your template, you can use the 'dependsOn' key to classify one resource as dependent on one or more resources. Azure Resource Manager reads your template, evaluates any dependencies you have set, and deploys resources according to their dependent order. You only need to define dependencies for resources that are deployed in the same template. The value of the dependsOn key can be set with a comma-separated, list of resource names.
[explanation]

----
##Multiple choice##

<<display_name:AZ400T05_MC_8; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following describes the correct way to reference a secret using Azure Key Vault?<<

( ) The Key Vault is referenced in the template, not parameter file.
( ) The Key Vault is referenced in both the template and in the parameter file.
(x) The Key Vault is referenced in the parameter file, not in the template.
( ) None of the above.

[explanation]
The Key Vault is referenced in the parameter file, not in the template, is the correct answer.

All other answers are incorrect because they potentially expose the secret in a publicly accessible template.

When you need to pass a secure value (like a password) as a parameter during deployment, you can retrieve the value from an Azure Key Vault. You can retrieve the value by referencing the secret in your parameter file. Storing the secret in the parameter file ensures that its value is never exposed, because you only reference the secret using its Key Vault ID.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_9; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following are benefits to using Azure Resource Manager templates?<<

(choose all that apply)

[x] Templates improve consistency
[x] Templates help express complex deployments
[x] Templates promote reuse
[x] Templates are linkable

[explanation]
All of the answers are correct.

Azure Resource Manager (ARM) templates improve consistency because templates provide a common language for describing your deployments. Regardless of which tool or SDK is used to deploy the template, the structure, format, and expressions inside the template remain the same. ARM templates help express complex deployments by allowing you to deploy multiple resources in a specific order, according to their dependencies. Templates promote reuse because you reuse the same templates across different areas of your infrastructure. Templates are linkable, which supports modularization, because you can write small templates, each of which defines a particular piece of your solution, and then combine them to create a complete system.
[explanation]

----
##Dropdown##

<<display_name:AZ400T05_DD_10; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following is used to list the Azure CLI commands that contain 'vm'?<<

[[
az list -q vm
az search -q vm
(az find -q vm)
az get -q vm
]]

[explanation]
'az find -q vm' is the correct answer.

All other answers are incorrect because they will not results in a list of the Azure CLI commands that contain 'vm'.

The Azure CLI lets you control many aspects of an Azure resource. Commands in the Azure CLI are structured in *groups* and *subgroups*. Each group represents a service provided by Azure, and the subgroups divide commands for these services into logical groupings. You can use 'az find' to see a list of the commands that can be applied to a particular subgroup. For example, to see a list of the commands applicable to virtual machines (VM), use 'az find' as follows: 'az find -q  vm'
[explanation]

----
##Multiple choice##

<<display_name:AZ400T05_MC_11; max_attempts:1; showanswer:never; weight:1>>

>>True or false: Within Availability Sets, Update Domains provide for the physical separation of workloads across different hardware in a datacenter?<<

( ) True
(x) False

[explanation]
False is the correct answer.

Within Availability Sets, Fault Domains provide for the physical separation of workloads across different hardware in a datacenter.

Update Domains are a *logical* section of the datacenter, implemented by software and logic. When a maintenance event occurs (such as a performance update or critical security patch applied to the host), the update is sequenced through Update Domains. Sequencing updates by using Update Domains ensures that the entire datacenter does not fail during platform updates and patching.

Fault Domains provide for the *physical* separation of your workload across different hardware in the datacenter. This includes power, cooling, and network hardware that supports the physical servers located in server racks. If the hardware that supports a server rack becomes unavailable, only that specific rack of servers would be affected by the outage.
[explanation]

----
##Multiple choice##

<<display_name:AZ400T05_MC_12; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following Azure offerings is used for hosting web applications, REST APIs, and mobile back ends?<<

( ) Azure Functions
( ) Application Insights
(x) Azure App Service
( ) Visual Studio App Center

[explanation]
Azure App Service is the correct answer.

The other answers are incorrect because:
Azure Functions is used for processing events with serverless code.
Application Insights. is used for detecting, triaging, and diagnosing issues in your web apps and services.
Visual Studio App Center used is for building, testing, releasing, and monitoring your apps from within a single software application.

Azure App Service is a Platform as Service offering on Azure, for hosting web applications, REST APIs, and mobile back ends. With Azure App Service you can create powerful cloud apps quickly within a fully managed platform. You can use Azure App Service to build, deploy, and scale enterprise-grade web, mobile, and API apps to run on any platform. Azure App Service ensures your application meet rigorous performance, scalability, security and compliance requirements, and benefit from using a fully managed platform for performing infrastructure maintenance.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_13; max_attempts:1; showanswer:never; weight:1>>

>>Web App for Containers can provide an ideal environment for which of the following scenarios?<<

( ) creating and managing groups of identical, load balanced VMs.
(x) running web apps that do not require extensive infrastructure control.
( ) running dedicated Azure VMs on dedicated Azure Virtual Networks
( ) scaling resources up or down using triggers based on load or performance metrics, or using a scheduled date and time.

[explanation]
Running web apps that do not require extensive infrastructure control is the correct answer.

The other answers are incorrect because:
Creating and managing groups of identical, load balanced VMs is best performed by Azure Virtual Machine Scale Sets.
Running dedicated Azure VMs on dedicated Azure Virtual Networks is performed using the Isolated Pricing Tier within you App Service plan.
Scaling resources up or down using triggers based on load or performance metrics, or using a scheduled date and time, is performed by autoscaling.

Web App for Containers provides an ideal environment to run web apps that do not require extensive infrastructure control. For Operations, Web App for Containers provide rich configuration features so developers can easily add custom domains, integrate with AAD authentication, add SSL certificates and more — all of which are crucial to web app development and management.

Web App for Containers from the Azure App Service also allow customers to use their own containers, and deploy them to Azure App Service as a web app. Similar to the Azure Web App solution, Web App for Containers eliminates time-consuming infrastructure management tasks during container deployment, updating, and scaling to help developers focus on coding and getting their apps to their end users faster. Furthermore, Web App for Containers provides integrated CI/CD capabilities with DockerHub, Azure Container Registry, and VSTS, as well as built-in staging, rollback, testing-in-production, monitoring, and performance testing capabilities to boost developer productivity.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_14; max_attempts:1; showanswer:never; weight:1>>

>>In Azure Functions, which of the following can add state and data persistence to stateless functions?<<

(choose two)

[x] the Durable Functions Extension.
[x] connecting to an Azure Storage service.
[ ] Logic Apps.
[ ] Event Grid.

[explanation]
The Durable Functions Extension, and connecting to an Azure Storage service are the correct answers.

The other answers are incorrect because:
Logic Apps automates access to, and use of, data across clouds.
Event Grid facilitates event delivery at massive scale.

Azure Functions are an implementation of the Functions-as-a-Service programming model on Azure, with additional capabilities. It is best practice to ensure that your functions are as stateless as possible. Stateless functions behave as if they have been restarted, every time they respond to an event. You should associate any required state information with your data instead. For example, an order being processed would likely have an associated state member. A function could process an order based on that state, update the data as required, while the function itself remains stateless. If you require stateful functions, you can use the Durable Functions Extension for Azure Functions or output persistent data to an Azure Storage service.
[explanation]
---
##Dropdown##

<<display_name:AZ400T05_DD_15; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence. Existing applications that you package and run as Service Fabric services (stateless) are called... ?<<

[[
Reliable Actor patterns
Container processes
Reliable Services
(Guest Executables)
]]

[explanation]
Guest Executables is the correct answer.

All other answers are incorrect.

Reliable Actors is a framework built on top of Reliable Services which implements the Virtual Actors design pattern. Containers can run in a similar way to guest executables, with an added capacity for restricting resource consumption per container. Reliable Services is a framework for creating services that use specific features provided by Azure Service Fabric.

Guest Executables are existing applications that you package and run as Service Fabric services (stateless). This makes the applications highly available, as Service Fabric keeps the instances of your applications running. Applications can be upgraded with no downtime, and Service Fabric can automatically roll back deployments if needed.
[explanation]

----
##Multiple choice##

<<display_name:AZ400T05_MC_16; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following may occur if Azure Service Fabric cannot comply with a Placement Constraint?<<

(x) The service will not run.
( ) Workloads become isolated from each other.
( ) N-tier applications are 'Lifted and shifted' into Azure Service Fabric.
( ) Services run on specific server configurations.

[explanation]
The service will not run is an correct answer.

All other answers are incorrect answers because they describe primary uses of Placement Constraints with Azure Service Fabric.

Placement Constraints can control which nodes in a cluster that a service can run on. Placement Constraints are primarily used to: Isolate workloads from each other; 'Lift and shift' an existing N-tier application into Azure Service Fabric; Run services on specific server configurations.

Placement Constraints can restrict Service Fabric's ability to balance overall cluster resource consumption. Make sure that your Placement Constraints are not too restrictive. Otherwise, if Service Fabric cannot comply with a Placement Constraint, your service will not run.
[explanation]

---
##Dropdown##

<<display_name:AZ400T05_DD_17; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence. With ____ Networking, the Azure Kubernetes Service (AKS) cluster is connected to existing virtual network resources and configurations.<<

[[
Basic
(Advanced)
]]

[explanation]
Advanced is the correct answer.

Basic is an incorrect answer.

In AKS, you can deploy a cluster to use either Basic Networking or Advanced Networking. With Basic Networking, the network resources are created and configured as the AKS cluster is deployed. With Advanced Networking, the AKS cluster is connected to existing virtual network resources and configurations.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_18; max_attempts:1; showanswer:never; weight:1>>

>>True or false: The kubectl Command Line Interface (CLI) can be used to deploy an application to Kubernetes?<<

(x) True
( ) False

[explanation]
True is the correct answer.

False in an incorrect answer.

It is possible to deploy an application to Kubernetes using the kubectl CLI, which can also be used to manage the cluster. By running kubectl on your build agent, you can deploy Kubernetes pods from Azure DevOps.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_19; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following architecture models/ styles is generally considered to be best suited to IoT and real-time systems?<<

( ) N-tier
( ) Web-queue-worker
( ) Microservices
( ) CQRS
(x) Event-driven
( ) Big data
( ) Big compute

[explanation]
Event-driven is the correct answer.

All other answers are incorrect.

Of all the architecture models/ styles listed, an Event-driven model is the most efficient for handling the real-time processing of data in high volumes data and at high velocity.

Architecture styles don't require the use of particular technologies, but some technologies are well-suited for certain architectures. For example, an event-driven architecture is generally considered to be best suited to IoT and real-time systems.

An N-tier architecture model is a natural fit for migrating existing applications that already use a layered architecture
A Web-queue-worker architecture model is suitable for relatively simple domains with some resource-intensive tasks.
The CQRS architecture model makes the most sense when it's applied to a subsystem of a larger architecture.
The Microservices model is deemed a natural fit for working with containers.
A Big data architecture model divides a very large dataset into chunks, performing paralleling processing across the entire set, for analysis and reporting.
Finally, the Big compute architecture model, also called high-performance computing (HPC), makes parallel computations across a large number (thousands) of cores.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_20; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following cloud service models provides simplicity, elastic scale, and potential cost savings?<<

( ) Infrastructure-as-a-Service (IaaS)
(x) Functions-as-a-Service (FaaS)
( ) Platform-as-a-Service (PaaS)

[explanation]
Functions-as-a-Service (FaaS) is the correct answer.

Infrastructure-as-a-Service (IaaS) and Platform-as-a-Service (PaaS) are incorrect answers.

Of the three cloud service models mentioned, FaaS provides simplicity, elastic scale, and potential cost savings, because you pay only for the time your code is running. IaaS provides the most control, flexibility, and portability. PaaS falls somewhere between the two.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_21; max_attempts:1; showanswer:never; weight:1>>

>>Within Azure Automation, which of the following is a PowerShell platform for managing your infrastructure using Configuration as Code?<<

( ) System Center Configuration Manager
( ) Azure Automation Utility
(x) Desired State Configuration
( ) Start/Stop VMs

[explanation]
Desired State Configuration is the correct answer.

All other answers are incorrect because:
System Center Configuration Manager is for managing devices and users, on-premises and in the cloud.
Azure Automation Utility contains a package for authoring Python within Azure Automation
Start/Stop VMs is a solution for starting and stopping Azure virtual machines according to user-defined schedules.

Within Azure Automation, Desired State Configuration (DSC) is a PowerShell platform for managing your infrastructure using Configuration as Code. Configuration management is a key capability of the Azure Automation service. DSC facilitates configuration management by allowing you to write, manage, and compile PowerShell DSC configurations, import DSC Resources, and assign configurations to target nodes, in the cloud. Other key capabilities of the Azure Automation service include: Process automation; Update Management; Start/Stop VMs; Source control integration; Automate resources in Amazon Web Services (AWS); Manage Shared resources; Running backups; Cross-platform support.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_22; max_attempts:1; showanswer:never; weight:1>>

>>How can you use Automation Accounts to segregate and limit the scope of access to resources within your solution?<<

( ) By closing your Azure Automation Account.
( ) By deactivating the "Create Azure Run As account" option.
( ) By signing in without subscription-owner access privileges.
(x) By creating multiple Automation Accounts.

[explanation]
By creating multiple Automation Accounts is the correct answer.

Closing your Azure Automation Account is incorrect because you need at least one open Azure Automation Account to use Azure Automation.
Deactivating the 'Create Azure Run As account' option is incorrect because this option must be enabled to create an Azure Automation Account.
Signing in without subscription-owner access privileges is incorrect because, as a safeguard, subscription-owner access is required to add an Azure Automation Account.

To minimize risks, it is recommended that you create multiple Automation Accounts. Creating multiple Automation Accounts helps to segregate and limit the scope of access to the resources within your solution. For example, you might use one Automation Account for development, another for production, and another for your on-premises environment. To start using the Azure Automation service, you must first create an Azure Automation Account. You need at least one Azure Automation Account to use Azure Automation. As a safeguard, subscription-owner access is required to add an Azure Automation Account. The 'Create Azure Run As account' option must also be enabled to create an Azure Automation Account.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_23; max_attempts:1; showanswer:never; weight:1>>

>>With Azure Automation Shared Resources, why you should try to create Global Assets?<<

(choose all that apply)

[ ] Global assets are specific to a single runbook.
[x] Reusing global assets saves time.
[x] Global assets can be used across your runbooks.
[x] Global assets reduce the number of manual edits you need to perform on individual runbooks.

[explanation]
The three correct answers are: Reusing global assets saves time; Global assets can be used across your runbooks; Global assets reduce the number of manual edits you need to perform on individual runbooks.

Global assets are specific to a single runbook, is an incorrect answer.

Global assets are not specific to a single runbook. As a best practice, you should always try to create Global Assets. Global assets can be used across your runbooks. Reusing global assets will save time by reducing the number of manual edits you need to perform on individual runbooks.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_24; max_attempts:1; showanswer:never; weight:1>>

>>True or false: You can convert a Graphical type runbook to a Textual type runbook, but not vice-versa?<<

( ) True
(x) False

[explanation]
False is the correct answer.

True is an incorrect answer.

You cannot convert a Graphical type runbook to a Textual type runbook, or vice-versa. Graphical type runbooks refer to Graphical and Graphical PowerShell Workflow runbooks. Graphical type runbooks are created and edited with the online graphical editor in Azure portal. Textual type runbooks are PowerShell, Windows PowerShell Workflow, and Python runbooks. Textual type runbooks are created and edited with the online text editor in Azure portal, or with an offline text editor.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_25; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following statements about runbooks are correct?<<

(choose all that apply)

[x] With Azure Automation, a runbook must be published before you can start it.
[ ] Runbooks must only be created in as PowerShell runbooks.
[x] Publishing a runbook makes it available for starting.
[x] Runbooks can also be combined to perform complex processes.

[explanation]
The correct answers are: With Azure Automation, a runbook must be published before you can start it; Publishing a runbook makes it available for starting; Runbooks can also be combined to perform complex processes.

Runbooks must only be created in PowerShell is an incorrect answer. Runbooks can be created as PowerShell, Graphical, Graphical PowerShell Workflow, Windows PowerShell Workflow, or Python runbooks.

With Azure Automation, a runbook must be published before you can start it. Publishing the runbook makes it available for starting. A runbook is a set of tasks that perform some automated process in Azure Automation. Processes within a runbook can be simple and runbooks can be combined to perform complex processes.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_26; max_attempts:1; showanswer:never; weight:1>>

>>True or false: You can import directly from the Runbook Gallery using Windows PowerShell?<<

( ) True
(x) False

[explanation]
False is the correct answer.

True is an incorrect answer.

You cannot import directly from the Runbook Gallery using Windows PowerShell.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_27; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following statements about starting runbooks with Webhook URLs in Azure Automation are correct?<<

(choose two)

[ ] You can provide custom a URL for a Webhook.
[x] A Webhook URL contains a security token for authenticating the client to start the runbook.
[x] You can only view a Webhook URL in the Azure portal at the time the Webhook is created.
[ ] You can edit a Webhook URL in the Azure portal.

[explanation]
The correct answers are: A Webhook URL contains a security token for authenticating the client to start the runbook; You can only view a Webhook URL in the Azure portal at the time the Webhook is created.

The other answers are incorrect because you *cannot* provide custom a URL for a Webhook, or edit a Webhook URL in the Azure portal.

The URL of the Webhook is a unique address. A client calls the URL with an HTTP POST request to start a runbook that is linked to the Webhook. The Webhook URL is generated automatically when you create the Webhook. You cannot specify a custom URL. The Webhook URL contains a security token that allows the runbook to be invoked by a third-party systems with no further authentication. For this reason, the URL should be treated like a password. For security reasons, you can only view the Webhook URL in the Azure portal at the time the Webhook is created. You should note the Webhook URL and store it in a secure location for future use with your runbooks.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_28; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following helps automate the distribution, orchestration, and completion of multi-device tasks, by arranging activities and leveraging the power of the PowerShell scripting syntax.<<

(x) Windows PowerShell Workflow
( ) Azure Automation State Configuration service
( ) PowerShell Integrated Scripting Environment (ISE) add-on
( ) Azure Service Fabric

[explanation]
Windows PowerShell Workflow is the correct answer.

All other answers are incorrect answers.

The Azure Automation State Configuration service is for creating and managing PowerShell Desired State Configurations (DSC).
The PowerShell Integrated Scripting Environment (ISE) add-on is for authoring Service Management Automation (SMA) runbooks in PowerShell ISE.
Azure Service Fabric is a distributed systems platform for packaging, deploying, and managing microservices applications and container orchestration.

Arranging activities into Windows PowerShell Workflows can leverage the power of the PowerShell scripting syntax. The automation capabilities of PowerShell enables Windows PowerShell Workflow to automate the distribution, orchestration, and completion of multi-device tasks, which frees users and administrators to focus on higher-level tasks.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_29; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following can highlight syntax errors, and distinguish between workflows and scripts, when writing workflows?<<

( ) Cloud Shell
( ) Language Understanding
(x) Windows PowerShell Integrated Scripting Environment (ISE)
( ) Azure Pipelines

[explanation]
Windows PowerShell Integrated Scripting Environment (ISE) is the correct answer.

Cloud Shell is an Azure product for streamlining Azure administration with a browser-based shell.
Language Understanding is an Azure, machine-based, learning service to build natural language understanding into apps.
Azure Pipelines is a DevOps service for building, testing, and deploying to any platform and cloud.

Windows PowerShell ISE auto compiles your workflow code, and allows you to save the artifact. The syntactic differences between scripts and workflows are significant, and Windows PowerShell ISE can distinguish workflows from scripts. Windows PowerShell ISE can also enforce strict adherence to the correct syntax, and highlight syntax errors. As a result, using Windows PowerShell ISE to write your workflows will save you significant coding and testing time. The key time-saving benefits to using Windows PowerShell IS for writing workflows are: Auto compiles your workflow code; Allows you to save the coded artifact; Enforces strict adherence to the correct workflow syntax; Highlights syntax errors; Supports workflows and scripts; Distinguishes between workflows and scripts.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_30; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following are features of Azure Automation State configuration?<<

(choose three)

[x] Built-in DSC pull server.
[x] Centralized management of DSC artifacts.
[x] Enhanced reporting and analyzes capabilities.
[ ] Supports WindowsOptionalFeature DSC resource in Windows 7.

[explanation]
The correct answers are: Built-in DSC pull server; Centralized management of DSC artifacts; Enhanced reporting and analyzes capabilities.

Supports WindowsOptionalFeature DSC resource in Windows 7, is an incorrect answer. The WindowsOptionalFeature DSC resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.

One of the main features of Azure Automation State configuration is a built-in DCS pull server. The built-in DSC pull server ensures that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in DSC pull server in Azure Automation eliminates the need to set up and maintain your own pull server.

A second feature of Azure Automation State configuration is the provision of centralized management for DSC artifacts. With Azure Automation State configuration you can manage all your DSC configurations, resources, and target nodes, from the Azure portal, or from PowerShell.

A third feature of Azure Automation State configuration is the provision of enhanced reporting and analyzes capabilities. Nodes that are managed with Azure Automation State Configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation State Configuration to send this data to your Log Analytics workspace.
[explanation]

---
##Dropdown##

<<display_name:AZ400T05_DD_31; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence. Chef's main architectural components are Chef Server, Chef Client and... ?<<

[[
Chef Facts
Chef Master
Chef Console Services
(Chef Workstation)
]]

[explanation]
Chef Workstation is the correct answer.

All other answers are incorrect answers.

Chef Facts, Chef Master, and Chef Console Services are not architectural components of Chef. Chef Facts, Chef Master, and Chef Console Services misrepresent terms used by the Puppet automation tool.

Chef has the following main architectural components. 'Chef Server' is the Chef management point. The two options for the Chef Server are 'hosted' and 'on-premises'. 'Chef Client (node)' is an agent that sits on the servers you are managing. 'Chef Workstation' is an Administrator workstation where you create Chef policies and execute management commands. You run the Chef 'knife' command from the Chef Workstation to manage your infrastructure.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_32; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence. In Chef Automate, you can define desired states, conduct violation detection audits, and generate reports, using... ?<<

( ) Habitat.
(x) InSpec.
( ) Facts.
( ) Console Services.

[explanation]
InSpec is the correct answer.

Habitat, Facts and Console Services are incorrect answers.

In Chef Automate, Habitat is for creating platform-independent build artifacts called 'habitats' for your applications. Facts are metadata used to determine the state of resources managed by the Puppet automation tool. Console Services is a web-based user interface for managing your system with the Puppet automation tool.

In Chef Automate, you can define desired states, conduct violation detection audits, and generate reports, using InSpec. InSpec is an open-source product that is integrated into the Chef Automate image available from Azure Marketplace. InSpec allows you to define desired states for your applications and infrastructure. InSpec can conduct audits to detect violations against your desired state definitions, and generate reports from its audit results.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_33; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following components of the Puppet automation platform provides a toolset for managing and configuring resources?<<

( ) Puppet Master
( ) Puppet Agent
(x) Console Services
(x) Facts

[explanation]
Console Services is the correct answer.

All other answers are incorrect because they refer to components of Puppet which do not provide a toolset for managing and configuring resources.

In the Puppet automation platform, Console Services is a toolset for managing user permissions (RBAC), and for configuring managed resources. It also includes a web-based user interface for managing your systems, i.e. the Puppet Enterprise (PE) Console UI. Puppet consists of the following additional core components. 'Puppet Master' acts as a center for Puppet activities and processes. 'Puppet Agent' runs on machines managed by Puppet, to facilitate management.  'Facts' are metadata used to determine the state of resources managed by Puppet. 'Console Services' provides a toolset for managing and configuring resources.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_34; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following are main elements of a Puppet Program (PP) Manifest file?<<

(choose three)

[x] Module
[ ] Recipes
[x] Class
[x] Resource

[explanation]
The correct answers are: Class, Resource and Module.

Recipes is an incorrect answer as recipes are used by the Chef automation platform.

The main elements of a Puppet Program (PP) Manifest file are Class, Resource and Module. Classes define related resources according to their classification, to be reused when composing other workflows. Resources are single elements of your configuration which you can specify parameters for. Modules are collection of all the classes, resources and other elements in a single entity.
[explanation]

----
##Checkbox##

<<display_name:AZ400T05_CB_35; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following statements about the Ansible platform are correct?<<

[ ] Ansible uses agents to communicate with target machines.
[x] Ansible is agent-less.
[x] Ansible uses SSH to communicate with target machines.
[ ] Ansible is closed source.

[explanation]
The correct answers are: Ansible is agent-less, and Ansible uses SSH to communicate with target machines.

Ansible uses agents to communicate with target machines, and Ansible is closed source, are incorrect answers.

Ansible is agent-less and does not use agents to communicate with target machines. Ansible is also open source, not closed source.

Ansible is agentless because you do not need to install an Agent on each of the target machines it manages. Ansible uses the Secure Shell (SSH) protocol to communicate with target machines. You choose when to conduct compliance checks and perform corrective actions, instead of using Agents and a Master to perform these operations automatically. With platforms that use agents, such as Puppet and Chef, you install an Agent on each target machine managed by the platform. Agents typically run as a background service and facilitate communication with a Master, which runs on a server. The Master uses information provided by Agents to conduct compliance checks and perform corrective actions automatically.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_36; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following are core components of Ansible?<<

(choose all that apply)

[x] Control Machine
[x] Managed Nodes
[x] Playbooks
[x] Modules#

[explanation]
All answers are correct.

Control Machine, Managed Nodes, Playbooks, and Modules, are core components of Ansible. Other core components are Inventory, Roles, Facts, and Plug-ins. Control Machine is for running configurations, with Ansible and Python installed.
Managed Nodes are resources managed by Ansible. Playbooks are ordered lists of Ansible tasks. Modules are small blocks of code within a Playbook that perform specific tasks. Inventory is list of managed nodes. Roles allow for the automatic and sequenced loading of variables, files, tasks and handlers. Facts are data points about the remote system which Ansible is managing. Plug-ins supplement Ansible's core functionality.
[explanation]

---
##Dropdown##

<<display_name:AZ400T05_DD_37; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence. To apply custom configurations to a Linux VM in Azure, as it boots for the first time, you can use... ?<<

[[
az configure
(the cloud-init package)
az policy
az deployment
]]

[explanation]
The correct answer is cloud-init.

All other answers are incorrect answers because they are commands used with the Azure Command Line Interface (CLI).

az configure is used with the Azure CLI for managing Azure CLI configurations.
az policy is for managing resource policies with the Azure CLI.
az deployment is used with the Azure CLI for managing Azure Resource Manager deployments at subscription scope.

Cloud-init is a package that is often used to add custom configurations to a Linux VM, as it boots for the first time. Cloud-init works across Linux distributions. In Azure, you can add custom configurations to a Linux VM with cloud-init and a configuration file (.txt). Any provisioning configuration information contained in the specified configuration file (.txt) is applied to the new VM, when the VM is created.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_38; max_attempts:1; showanswer:never; weight:1>>

>>With the cloud-init package, which of the following parameters passes the name of a configuration file (.txt)?<<

( ) --service-principal
( ) --use-device-code
(x) --custom-data
( ) --identity

[explanation]
The correct answer is --custom-data.

All other answers are incorrect answers because they are parameters that are appended to the az login command for logging in to Azure with the Azure Command Line Interface (CLI).

The --service-principal parameter specifies a credential, representing a service principal, for logging in to Azure with the Azure CLI and az login command.
The --use-device-code parameter tells the az login command to use CLI's old authentication flow based on device code, when logging in to Azure with the Azure CLI.
The --identity parameter is used to log in to Azure using a VM's system assigned identity, with the Azure CLI and az login command.

In Azure, you can add custom configurations to a Linux VM with cloud-init by appending the --custom-data parameter, and passing the name of a configuration file (.txt), to the az vm create command. The --custom-data parameter passes the name of the configuration file (.txt) as an argument to cloud-init. Then, cloud-init applies Base64 encoding to the contents of the configuration file (.txt), and sends it along with any provisioning configuration information that is contained within the configuration file (.txt). Any provisioning configuration information contained in the specified configuration file (.txt) is applied to the new VM, when the VM is created. The YML syntax is used within the configuration file (.txt) to define any provisioning configuration information that needs to be applied to the VM.
[explanation]

---
