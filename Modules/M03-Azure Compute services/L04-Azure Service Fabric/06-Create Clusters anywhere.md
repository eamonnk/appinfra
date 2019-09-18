

You can create Service Fabric clusters in many environments:

- Windows operating system
- Linux operating system
- On premises 
- In the cloud
- On one machine 
- On multiple servers

There are two distinct versions of the Service Fabric binaries, one that runs on the Windows operating system and one for Linux. Both are restricted to the 64-bit platform. 


> **Note**: For more details see the <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-deploy-anywhere" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create Service Fabric clusters on Windows Server or Linux</span></a> page.


#### Windows Server
You can deploy a cluster manually by using a set of PowerShell tools on a prepared group of servers, and then running Windows Server 2016 or Windows Server 2019. This approach is called a *Service Fabric standalone cluster*. 

It's also possible to create a cluster in Azure. You can do this using the Azure Portal, or by using an Azure Resource Manager template. This will create a cluster and everything that's needed to run applications on it.

Finally, there is an option to create a cluster specifically for development use that runs on just one machine simulating multiple servers. This is called a *local development cluster*, and it allows developers to debug their applications before deploying them to a production cluster.

> Note: It's important to know that for every type of deployment, the actual Service Fabric binaries are the same. This means that an application that works on a development cluster will also work on an on-premises or cloud-hosted cluster without requiring modifications to the code. This is similar to the portability that containerization offers.

#### Linux
At the time of this writing, Service Fabric for Linux has been released. However, it does not yet have complete feature parity between Windows and Linux. This means that some Windows features are not available on Linux. For example, you cannot create a Service Fabric anywhere cluster, and all programming models are in preview (including Java/C# Reliable Actors, Reliable Stateless Services, and Reliable Stateful Services).

You can create a Linux cluster in Azure and create a local development cluster on the Linux Ubuntu 16.04 and Red Hat Enterprise Linux 7.4 (preview support) operating systems.


For more details, see the <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-linux-windows-differences" target="_blank"><span style="color: #0066cc;" color="#0066cc">Differences between Service Fabric on Linux and Windows</span></a> page.


> **Note**: Standalone clusters currently aren't supported for Linux. Linux is supported on one-box for development and Linux virtual machine clusters.
