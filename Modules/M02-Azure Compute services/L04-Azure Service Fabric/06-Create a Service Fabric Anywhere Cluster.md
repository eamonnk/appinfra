

![Virtual machines have an arrow labeled PowerShell pointing to Service Fabric Cluster.](../../Linked_Image_Files\3.1.2_Standalone_Cluster.png)

Creating a standalone Azure Service Fabric cluster requires you to provision the hardware resources up front. After you have created and configured the required machines, you can use PowerShell to create a cluster. The required scripts and binaries can be downloaded in a single package, the Service Fabric standalone package.

At this time, only Windows Server can be used to create a production cluster. Linux clusters can only be created as development clusters (on a single machine) and as Azure clusters on multiple virtual machines.

#### Process

The basic process of creating a standalone cluster is:

1. **Prepare**

    You need to plan the required amount of server resources. Those servers need to meet the minimum requirements for Service Fabric.

    Fault domains and upgrade domains need to be defined. 

    The software prerequisites need to be installed. 

    The configuration file `ClusterConfig.json` needs to be provided with IP addresses of servers that must become cluster nodes.

2. **Validate**

    A validation script `TestConfiguration.ps1` is provided as part of the package. It has a Best practices analyzer that can validate some of the criteria on your resources.

3. **Create**

    A creation script `CreateServiceFabricCluster.ps1` is also provided. Running this will create the entire cluster for you on all designated machines.

4. **Upgrade**

    You can run the PowerShell script `Start-ServiceFabricClusterUpgrade` that is installed on the nodes as part of the deployment of the cluster to upgrade the cluster software to a specific version. 

5. **Remove**

    If you need to remove a cluster, the script `RemoveServiceFabricCluster.ps1` will help you do that.


You'll likely add your own public IP address and load balancer to this cluster, if you need to run services that are reachable over the internet.