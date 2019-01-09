Scaling Azure Clusters

#### Some definitions

Before we talk about scaling, let's briefly explain some concepts:

- **Scaling in and out**

    Removing and adding nodes to the cluster.

- **Scaling up and down**

    Changing the size (SKU) of the VMs that make up the cluster.

- **Node types**

    One or more individual VM scale sets that make up the cluster.

- **Fault domain**

    This is a hierarchical structure of levels of infrastructure in which faults can occur. For example, faults can happen in disk drives, machines, power supplies, server racks and entire data centers. To create a system that is highly available, you must consider these fault domains. Having two nodes that share a fault domain means they share a single point of failure.

- **Upgrade domain**

    A policy that describes groups of nodes that will be upgraded simultaneously. Nodes in different upgrade domains will not be upgraded at the same time. This means that upgrade domains are useful when performing rolling upgrades of your software. One by one, every upgrade domain will be processed.


    ![ud fd](../../Linked_Image_Files\3.5.2_UD_FD.png)

    ​

    For example, in the image above, you see six nodes. Imagine that node pairs 1/2, 3/4, and 5/6 each share a server rack, which means that they share a fault domain. Then, by policy, node pairs 1/6, 2/3, and 4/5 were put in upgrade domains. This means that changes to these nodes are applied simultaneously. This includes changes to the cluster software and to running services. By upgrading two nodes at the same time, they complete quickly. By adding more upgrade domains, your upgrades become more granular, and because of that, have lower impact. The most commonly used setup is to have one upgrade domain for one fault domain.

    ​

    ![](../../Linked_Image_Files\3.5.2_UD_FD2.png)

    This means that upgrades are applied to one node at a time. When services are deployed to multiple fault domains, and correctly configured upgrade domains, they are able to cope with node failures, even during upgrades.

### Boundaries

You can grow or shrink the number of servers that define the cluster by changing the size of a VM scale set. There are some restrictions that apply. 

#### Lower boundary
Earlier in this module, you learned that one of the platform services of Service Fabric is a distributed data store. Data stored on one node is replicated to a quorum (majority) of secondary nodes. This means that to work properly, you'll need to have multiple healthy nodes in your cluster. The precise number needed depends on the desired reliability of your services.

#### Upper boundary in Azure

VM scale sets are limited to 1,000 Virtual Machines when using existing platform images. In Azure, Service Fabric can scale up to 100 nodes in each scale set.

#### Durability levels in Azure

Whether Service Fabric can automatically deal with infrastructural changes depends on the cluster's configured durability level. The durability level indicates the level of privileges Service Fabric has to influence Azure infrastructural operations on the cluster's underlying VMs.

Three durability levels exist:
1. **Bronze**

    Durability level Bronze means no privileges. This is the default value. Changes to the scale set will be applied to all instances simultaneously.

2. **Silver**

    Durability level Silver means that Service Fabric can postpone changes on VMs for 30 minutes per upgrade domain. At this time, this level cannot be configured.

3. **Gold**

     Durability level Gold means that Service Fabric can postpone changes on VMs for 120 minutes per upgrade domain. Using Silver or Gold will enable you to make infrastructural changes to your VM scale set one upgrade domain at a time.


#### Adding or changing nodes in Azure

The capacity of your Azure cluster can be extended by simply increasing the VM scale set capacity. This can be done by using PowerShell, Azure Resource Manager templates, and by using code. Changing the SKU influences all cluster nodes, so whether you can do this depends on the configured durability level. When you use Silver or Gold levels, you can just do it; when using Bronze, you'll have some downtime because all VMs are upgraded simultaneously.

Unlike ACS clusters, the scale sets of a Service Fabric cluster can be configured to scale automatically based on performance counter metrics.

#### Adding nodes in standalone clusters

Scaling up a standalone cluster must be done by also using PowerShell scripts. Running the script `AddNode.ps1` on a prepared server will add it to an existing cluster.

#### Removing nodes in Azure

Although adding nodes to an Azure cluster is a matter of increasing the scale set capacity, removing them can be more complicated. Removing nodes from a cluster has implications for the distributed data store that holds the Reliable Collections of your services. Decreasing the instance count of your VM scale set results in the removal of cluster nodes. The impact of this depends on the durability level.
​     
If you're using the Bronze durability level, you must notify Service Fabric beforehand about your intention to remove a node. This instructs Service Fabric to move services and data away from the node. In other words, it drains the node. 

Next, you need to remove that node from the cluster. You must run the PowerShell script `Disable-ServiceFabricNode` for each node that you want to remove, and wait for Service Fabric to complete the operation.

If you don't properly remove the node from the cluster, Service Fabric will assume that the nodes have simply failed and will return later, after reporting them as having the status *Down*.

![In the Service Fabric Cluster blade, five nodes display with two of the nodes reporting with a status of down.](../../Linked_Image_Files\3.5.2_Scale_down.png)

Of course, this can also be done by using code.

#### Removing nodes from standalone clusters.

Removing nodes is somewhat different from the process in Azure clusters. Instead of executing `Disable-ServiceFabricNode`, you execute the script `RemoveNode.ps1` on the server that you want to remove.

>Due to a known issue, your node might remain visible with status ***Down*** in the Service Fabric explorer and in queries on the cluster.