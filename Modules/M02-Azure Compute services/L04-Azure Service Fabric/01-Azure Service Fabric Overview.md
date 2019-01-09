<h1><strong><span style="color: #0000CD;">Azure Service Fabric Overview</span></strong></h1>

In Module 2, you learned how clustered computing can help run containerized applications at scale. Another way to accomplish this is by using Azure Service Fabric. This product also uses a cluster of servers on which to run workloads. The main difference is that those workloads don't have to be containers.

### Introducing Azure Service Fabric

Azure Service Fabric is a distributed platform that allows you to package, deploy, and manage microservices. Service Fabric enables you to run applications on a pool of servers, at high density, to make optimal use of the cluster's resources. It comes with a software development kit (SDK) that enables development teams to create the applications. It also offers a set of tools that enable application deployments and cluster provisioning.

![For clusters anywhere, Five boxes overlay a second box: Web Apps, including .NET Core and OWIN; Reliability Actors; Reliability Services; Guest Executables (Any Code); Containers (Windows Containers and Docker). The box below contains Always On Availability, Orchestration, Programming Models, Health and Monitoring, Dev and Ops Tooling, and Auto Scaling.](../../Linked_Image_Files\3.1.2_Clusters_anywhere.png)

#### Applications and services

Service Fabric applications consist of one or more services that work together to automate business processes. Services are executables that run independently of other services, and are composed of code, configuration, and data. Each element is separately versionable and deployable. 

