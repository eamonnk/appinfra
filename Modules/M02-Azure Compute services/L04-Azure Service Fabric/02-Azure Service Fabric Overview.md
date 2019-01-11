

Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable. It has two primary functions which are providing for 

- microservices applications
- container orchestratration

Developers and administrators can avoid complex infrastructure problems and focus on implementing mission-critical, demanding workloads that are scalable, reliable, and manageable. 

It is designed for modern cloud native application. Service Fabric represents the next-generation platform for building and managing these enterprise-class, tier-1, cloud-scale applications running in containers.



### Where and what can Service fabric run?
Service Fabric runs everywhere. You can create clusters for Service Fabric in many environments, including Azure or on premises, on Windows Server, or on Linux. You can even create clusters on other public clouds. In addition, the development environment in the SDK is identical to the production environment, with no emulators involved. In other words, what runs on your local development cluster deploys to the clusters in other environments

<p style="text-align:center;"><img src="../Linked_Image_Files/servicefabricoverview.png" alt="Image representing the functionality and use cases for Azure Service Fabric. Contains a banner stating it support containers and microservices. The box below contains Lifecycle management, Always On Availability, Orchestration, Programming Models, Health and Monitoring, Dev and Ops Tooling, and Auto Scaling, and then below that are images represneitng Linus and Windows, and local dev machine, Azure, On-premises Data centers and Other cloud platform, indicating where it can be run i.e. anywhere"></p>

### Applications and services

Service Fabric enables you to build and manage scalable and reliable applications composed of microservices that run at high density on a shared pool of machines, which is referred to as a cluster. 

It provides a sophisticated, lightweight runtime to build distributed, scalable, stateless, and stateful microservices running in containers. It also provides comprehensive application management capabilities to provision, deploy, monitor, upgrade/patch, and delete deployed applications including containerized services

### Key capabilities
By using Service Fabric, you can:
- Deploy to Azure or to on-premises datacenters that run Windows or Linux with zero code changes. Write once, and then deploy anywhere to any Service Fabric cluster.
- Develop scalable applications that are composed of microservices by using the Service Fabric programming models, containers, or any code.
- Develop highly reliable stateless and stateful microservices. Simplify the design of your application by using stateful microservices. 
- Use the novel Reliable Actors programming model to create cloud objects with self contained code and state.
- Deploy and orchestrate containers that include Windows containers and Linux containers. Service Fabric is a data aware, stateful, container orchestrator.
- Deploy applications in seconds, at high density with hundreds or thousands of applications or containers per machine.
- Deploy different versions of the same application side by side, and upgrade each application independently.
- Manage the lifecycle of your applications without any downtime, including breaking and nonbreaking upgrades.
- Scale out or scale in the number of nodes in a cluster. As you scale nodes, your applications automatically scale.
- Monitor and diagnose the health of your applications and set policies for performing automatic repairs.
- Watch the resource balancer orchestrate the redistribution of applications across the cluster. Service Fabric recovers from failures and optimizes the distribution of load based on available resources.


> **Note**: Service Fabric is currently undergoing a big transition to open development. The goal is to move the entire build, test, and development process to GitHub. You can view, investigate and contribute on the 
<a href="https://github.com/Microsoft/service-fabric/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> https://github.com/Microsoft/service-fabric/</span></a> page. There are also many sample files and scenarios to help in deployment and configuration.