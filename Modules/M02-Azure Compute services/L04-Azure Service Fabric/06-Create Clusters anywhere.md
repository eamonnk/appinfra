



You can create Service Fabric clusters in many environments, including in Windows and on Linux, on-premises and in the cloud, and on one machine or multiple servers.

There are two distinct versions of the Service Fabric binaries, one that runs on Windows and one for Linux. Both are restricted to the 64-bit platform.

![For clusters anywhere, Five boxes overlay a second box: Web Apps, including .NET Core and OWIN; Reliability Actors; Reliability Services; Guest Executables (Any Code); Containers (Windows Containers and Docker). The box below contains Always On Availability, Orchestration, Programming Models, Health and Monitoring, Dev and Ops Tooling, and Auto Scaling.](../Linked_Image_Files\servicefabricoverview.png)


> **Note**: For more details, see the <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-anywhere" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create Service Fabric clusters on Windows Server or Linux</span> page.</a>


#### Windows
You can deploy a cluster manually by using a set of PowerShell tools on a prepared group of servers, running Windows Server 2012 R2 or 2016. This approach is called a **Service Fabric standalone cluster**.

It's also possible to create a cluster in Azure. You can do this using the Azure Portal, or using an Azure Resource Manager template. This will create a cluster and everything that's needed to run applications on it.

Finally, there is an option to create a cluster specifically for development use that runs on just one machine, simulating multiple servers. This is called a **local development cluster**, and it allows developers to debug their applications before deploying them to a production cluster.

> **Note**: It's important to know that for every type of deployment, the actual Service Fabric binaries are the same. This means that an application that works on a development cluster will also work on an on-premises or cloud hosted cluster, without requiring modifications to the code. This is similar to the portability that containerization offers.

#### Linux
At the time of this writing, Service Fabric for Linux is released, but there is not complete feature parity yet between Windows and Linux. This means that some features of the Windows version are not available on Linux. For instance, you cannot create a **Service Fabric anywhere** cluster, and all programming models are in preview (including Java/C# Reliable Actors, Reliable Stateless Services, and Reliable Stateful Services).

It is possible to create a Linux cluster in Azure and to create a local development cluster on the following operating systems
- Linux Ubuntu 16.04
- Red Hat Enterprise Linux 7.4 (preview support)


For more details, see the <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-linux-windows-differences" target="_blank"><span style="color: #0066cc;" color="#0066cc">Differences between Service Fabric on Linux and Windows</span> page.</a>


> **Note**: Standalone clusters currently aren't supported for Linux. Linux is supported on one-box for development and Azure Linux multi-machine clusters.
