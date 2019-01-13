# What are review questions? #

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Multiple choice##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following Azure products provides management capabilities for applications that run across multiple Virtual Machines, and allows for the automatic scaling of resources, and load balancing of traffic?<<

( ) Azure Service Fabric
(x) Virtual Machine Scale Sets
( ) Azure Kubernetes Service
( ) Virtual Network

[explanation]
Virtual Machine Scale Sets is the correct answer.

All other answers are incorrect.

Azure Service Fabric is for developing microservices and orchestrating containers on Windows or Linux.
Azure Kubernetes Service (AKS) simplifies the deployment, management, and operations of Kubernetes.
Virtual Network is for setting up and connecting virtual private networks.

With Azure VMs, scale is provided for by Virtual Machine Scale Sets (VMSS). Azure VMSS let you create and manage groups of identical, load balanced VMs. The number of VM instances can increase or decrease automatically, in response to demand or a defined schedule. Azure VMSS provide high availability to your applications, and allow you to centrally manage, configure, and update large numbers of VMs. With Azure VMSS, you can build large-scale services for areas such as compute, big data, and container workloads.
[explanation]

---
##Checkbox##

<<display_name:Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Availability sets are made up of which of the following?<<

(choose two)

[x] Update Domains
[ ] Azure AD Domain Services
[x] Fault Domains
[ ] Event Domains

[explanation]
Update Domains and Fault Domains are the correct answers.

Azure AD Domain Services and Event Domains are incorrect answers.

Azure AD Domain Service provides managed domain services to a Windows Server Active Directory in Azure. An event domain is a tool for managing and publishing information.

Update Domains are a *logical* section of the datacenter, implemented by software and logic. When a maintenance event occurs (such as a performance update or critical security patch applied to the host), the update is sequenced through Update Domains. Sequencing updates by using Update Domains ensures that the entire datacenter does not fail during platform updates and patching.

Fault Domains provide for the *physical* separation of your workload across different hardware in the datacenter. This includes power, cooling, and network hardware that supports the physical servers located in server racks. If the hardware that supports a server rack becomes unavailable, only that specific rack of servers would be affected by the outage.
[explanation]

---
##Dropdown##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Complete the following sentence: Azure App Service is an Azure Platform-as-Service offering that is used for... ?<<

[[
processing events with serverless code.
detecting, triaging, and diagnosing issues in your web apps and services.
building, testing, releasing, and monitoring your apps from within a single software application.
(hosting web applications, REST APIs, and mobile back ends.)
]]

[explanation]
Hosting web applications, REST APIs, and mobile back ends, is the correct answer.

The other answers are incorrect because:
Processing events with serverless code is performed by Azure Functions.
Detecting, triaging, and diagnosing issues in your web apps and services is performed by Application Insights.
Building, testing, releasing, and monitoring your apps from within a single software application is performed by Visual Studio App Center.

Azure App Service is a Platform as Service offering on Azure, for hosting web applications, REST APIs, and mobile back ends. With Azure App Service you can create powerful cloud apps quickly within a fully managed platform. You can use Azure App Service to build, deploy, and scale enterprise-grade web, mobile, and API apps to run on any platform. Azure App Service ensures your application meet rigorous performance, scalability, security and compliance requirements, and benefit from using a fully managed platform for performing infrastructure maintenance.
[explanation]

---
##Checkbox##

<<display_name:Review Question 4; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are features of Web App for Containers?<<

(choose all that apply)

[x] Deploys containerized applications using Docker Hub, Azure Container Registry, or private registries.
[x] Incrementally deploys apps into production with deployment slots and slot swaps.
[x] Scales out automatically with auto-scale.
[x] Uses the App Service Log Streaming feature to allow you to see logs from your application.
[x] Supports PowerShell and Win-RM for remotely connecting directly into your containers.

[explanation]
All of the answers are correct.

Web App for Containers from the Azure App Service allows customers to use their own containers, and deploy them to Azure App Service as a web app. Similar to the Azure Web App solution, Web App for Containers eliminates time-consuming infrastructure management tasks during container deployment, updating, and scaling to help developers focus on coding and getting their apps to their end users faster. Furthermore, Web App for Containers provides integrated CI/CD capabilities with DockerHub, Azure Container Registry, and VSTS, as well as built-in staging, rollback, testing-in-production, monitoring, and performance testing capabilities to boost developer productivity.

For Operations, Web App for Containers also provides rich configuration features so developers can easily add custom domains, integrate with AAD authentication, add SSL certificates and more — all of which are crucial to web app development and management. Web App for Containers provides an ideal environment to run web apps that do not require extensive infrastructure control.
[explanation]

----
##Multiple choice##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements is best practice for Azure Functions?<<

( ) Azure Functions should be stateful.
(x) Azure Functions should be stateless.

[explanation]
Azure Functions should be stateless is the correct answer.

Azure Functions should be stateful is an incorrect answer.

Azure Functions are an implementation of the Functions-as-a-Service programming model on Azure, with additional capabilities. It is best practice to ensure that your functions are as stateless as possible. Stateless functions behave as if they have been restarted, every time they respond to an event. You should associate any required state information with your data instead. For example, an order being processed would likely have an associated state member. A function could process an order based on that state, update the data as required, while the function itself remains stateless. If you require stateful functions, you can use the Durable Functions Extension for Azure Functions or output persistent data to an Azure Storage service.
[explanation]

---
