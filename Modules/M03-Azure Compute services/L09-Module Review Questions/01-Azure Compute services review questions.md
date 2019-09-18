

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Multiple Choice##

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

Update Domains are a logical section of the datacenter, implemented by software and logic. When a maintenance event occurs (such as a performance update or critical security patch applied to the host), the update is sequenced through Update Domains. Sequencing updates by using Update Domains ensures that the entire datacenter does not fail during platform updates and patching.

Fault Domains provide for the physical separation of your workload across different hardware in the datacenter. This includes power, cooling, and network hardware that supports the physical servers located in server racks. If the hardware that supports a server rack becomes unavailable, only that specific rack of servers would be affected by the outage.
[explanation]

---

##DropDown##

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

---

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

##Checkbox##

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following features are supported by Azure Service Fabric?<<

(choose all that apply)

[x] Reliable Services
[x] Reliable Actor patterns
[x] Guest Executables
[x] Container processes

[explanation]
All of the answers are correct.

Reliable Services is a framework for creating services that use specific features provided by Azure Service Fabric. The two distinct types of Reliable Services you can create are stateless services and stateful services.

Reliable Actors is a framework built on top of Reliable Services which implements the Virtual Actors design pattern. An Actor encapsulates a small piece of a state or behavior. The state of an Actor can be volatile, or it can be kept persistent in a distributed store. This store can be memory-based or on a disk.

Guest Executables are existing applications that you package and run as Service Fabric services (stateless). This makes the applications highly available, as Service Fabric keeps the instances of your applications running. Applications can be upgraded with no downtime, and Service Fabric can automatically roll back deployments if needed.

Containers can be run in a way that is similar to running guest executables. Furthermore, with containers, Service Fabric can restrict resource consumption per container (by CPU processes or memory usage, for example). Limiting resource consumption per service allows you to achieve higher densities on your cluster.
[explanation]

---

##Checkbox##

<<display_name:Review Question 7; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following describe primary uses for Placement Constraints?<<

(choose all that apply)

[x] Isolate workloads from each other
[x] Control which nodes in a cluster that a service can run on
[x] ‘Lift and shift’ an existing N-tier application into Azure Service Fabric.
[ ] Describe resources that nodes have, and that services consume, when they are run on a node.

[explanation]
The correct answers are: Isolate workloads from each other, control which nodes in a cluster that a service can run on, and ‘Lift and shift’ an existing N-tier application into Azure Service Fabric.

Describe resources that nodes have, and that services consume, when they are run on a node, is an incorrect answer. Metrics are used to describe resources that nodes have, and services consume, when they are run on a node.

Placement Constraints can control which nodes in a cluster that a service can run on. You can define any set of properties by node type, and then set constraints for them. Placement Constraints are primarily used to: Isolate workloads from each other; 'Lift and shift' an existing N-tier application into Azure Service Fabric; Run services on specific server configurations.

Placement Constraints can restrict Service Fabric's ability to balance overall cluster resource consumption. Make sure that your Placement Constraints are not too restrictive. Otherwise, if Service Fabric cannot comply with a Placement Constraint, your service will not run.
[explanation]

---

##Checkbox##

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are network models for deploying a clusters in Azure Kubernetes Service (AKS)?<<

(choose two)
[x] Basic Networking
[ ] Native Model
[x] Advanced Networking
[ ] Resource Model

[explanation]
Basic Networking and Advanced Networking are correct answers.

Native Model and Resource Model are incorrect answers because these are two deployment models supported by Azure Service Fabric.

In AKS, you can deploy a cluster to use either Basic Networking or Advanced Networking. With Basic Networking, the network resources are created and configured as the AKS cluster is deployed. Basic Networking is suitable for small development or test workloads, as you don't have to create the virtual network and subnets separately from the AKS cluster. Simple websites with low traffic, or to lift and shift workloads into containers, can also benefit from the simplicity of AKS clusters deployed with Basic Networking.

With Advanced Networking, the AKS cluster is connected to existing virtual network resources and configurations. Advanced Networking allows for the separation of control and management of resources. When you use Advanced Networking, the virtual network resource is in a separate resource group to the AKS cluster. For most production deployments, you should plan for and use Advanced Networking.
[explanation]

---

##Multiple choice##

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True or false: containers are a natural fit for an event-driven architecture?<<

( ) True
(x) False

[explanation]
False is the correct answer.

True is an incorrect answer.

Architecture styles don't require the use of particular technologies, but some technologies are well-suited for certain architectures. For example, containers are a natural fit for microservices, and an event-driven architecture is generally best suited to IoT and real-time systems.

An N-tier architecture model is a natural fit for migrating existing applications that already use a layered architecture
A Web-queue-worker architecture model is suitable for relatively simple domains with some resource-intensive tasks.
The CQRS architecture model makes the most sense when it's applied to a subsystem of a larger architecture.
A Big data architecture model divides a very large dataset into chunks, performing paralleling processing across the entire set, for analysis and reporting.
Finally, the Big compute architecture model, also called high-performance computing (HPC), makes parallel computations across a large number (thousands) of cores.
[explanation]

---

##Multiple choice##

<<display_name:Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following cloud service models provides the most control, flexibility, and portability?<<

(x) Infrastructure-as-a-Service (IaaS)
( ) Functions-as-a-Service (FaaS)
( ) Platform-as-a-Service (PaaS)

[explanation]
Infrastructure-as-a-Service (IaaS) is the correct answer.

Functions-as-a-Service (FaaS) and Platform-as-a-Service (PaaS) are incorrect answers.

Of the three cloud service models mentioned, IaaS provides the most control, flexibility, and portability.
FaaS provides simplicity, elastic scale, and potential cost savings, because you pay only for the time your code is running. PaaS falls somewhere between the two.
[explanation]

---
