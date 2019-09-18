

Before we talk about scaling, let's briefly explain some concepts:

- *Scaling in and out* is the process of removing and adding nodes to the cluster.

- *Scaling up and down* is the process of changing the size (SKU) of the VMs that make up the cluster.

- *Node types* are one or more individual VM scale sets that make up the cluster.

- *Fault domain* is a hierarchical structure of infrastructure levels in which faults can occur. For example, faults can happen on disk drives, machines, power supplies, or server racks, and in entire data centers. To create a system that is highly available, you must consider these fault domains. Having two nodes that share a fault domain means they share a single point of failure.

- *Upgrade domain* is a policy that describes groups of nodes that will be upgraded simultaneously. Nodes in different upgrade domains will not be upgraded at the same time. This means that upgrade domains are useful when performing rolling upgrades of your software. One by one, every upgrade domain will be processed.


    ​<p style="text-align:center;"><img src="../Linked_Image_Files/3.5.2_UD_FD.png" alt="image representing update domain and fault domain as described in the following paragraph."></p>

    For example, in this image you see six nodes. Imagine that node pairs one and two, three and four, and five and six each share a server rack, which means that they share a fault domain. Then, by policy, node pairs one and six, two and three, and four and five were put in upgrade domains. This means that changes to these node pairs are applied simultaneously. This includes changes to the cluster software and to running services. 
	
	By upgrading two nodes at the same time, they complete quickly. By adding more upgrade domains, your upgrades become more granular, and because of that, have a lower impact. The most commonly used setup is to have one upgrade domain for one fault domain.

    ​
  ​<p style="text-align:center;"><img src="../Linked_Image_Files/3.5.2_UD_FD2.png" alt="image representing update domain and fault domain in a changed state as described in the following paragraph."></p>


    This means that as exhibited in this image, upgrades are applied to one node at a time. When services are deployed to both multiple fault domains and correctly configured upgrade domains, they are able to manage node failures, even during upgrades.

### Boundaries

You can grow or shrink the number of servers that define in the cluster by changing the size of a VM scale set. However, there are some restrictions that apply. 

#### Lower boundary
Earlier in this module, you learned that one of the platform services of Service Fabric is a distributed data store. This means that data stored on one node is replicated to a quorum (majority) of secondary nodes. to work properly, you'll need to have multiple healthy nodes in your cluster. The precise number needed depends on the desired reliability of your services.

#### Upper boundary in Azure

When using existing platform images, VM scale sets are limited to 1,000 VMs. In Azure, Service Fabric can scale up to 100 nodes in each scale set.

#### Durability levels in Azure

Whether Service Fabric can automatically manage infrastructural changes depends on the cluster's configured durability level. The durability level indicates the level of privileges Service Fabric has to influence Azure infrastructural operations on the cluster's underlying VMs.

There are three durability levels, as exhibited in the following table.

| Durability tier |Required minimum number of VMs|Supported VM SKUs|Updates you make to your virtual machine scale set|Updates and maintenance initiated by Azure|
|---|---|---|---|---|
|Gold|5|Full-node SKUs dedicated to a single customer (for example, L32s, GS5, G5, DS15_v2, D15_v2)|Can be delayed until approved by the Service Fabric cluster|Can be paused for 2 hours per update domain to allow additional time for replicas to recover from earlier failures|
|Silver|5|VMs of single core or above|Can be delayed until approved by the Service Fabric cluster|Cannot be delayed for any significant period of time|
|Bronze|1|All|Will not be delayed by the Service Fabric cluster|Cannot be delayed for any significant period of time|



#### Adding or changing nodes in Azure

You can extend your Azure cluster capacity simply by increasing the VM scale set capacity. You can do this by using PowerShell, Azure Resource Manager templates, and by code. Changing the SKU influences all cluster nodes, so whether you can do this depends on the configured durability level. When you use Silver or Gold levels, you can do this, whereas when using the Bronze level, you'll have some downtime because all VMs upgrade simultaneously.

Unlike Azure Access Control (ACS) clusters, you can configure Service Fabric cluster scale sets to scale automatically based on performance counter metrics.

#### Adding nodes in standalone clusters

Scaling up a standalone cluster also must be done using PowerShell scripts. Running the script `AddNode.ps1` on a prepared server will add it to an existing cluster.

#### Removing nodes in Azure

Although adding nodes to an Azure cluster is a matter of increasing the scale set capacity, removing them can be more complicated. Removing nodes from a cluster has implications for the distributed data store that contains the Reliable Collections of your services. Decreasing the instance count of your VM scale set results in the removal of cluster nodes. The impact of this depends on the durability level.
​     
If you're using the Bronze durability level, you must notify Service Fabric beforehand of your intention to remove a node. This instructs Service Fabric to move services and data away from the node. In other words, it drains the node. 

Next, you need to remove that node from the cluster. You must run the PowerShell script `Disable-ServiceFabricNode` for each node that you want to remove, and wait for Service Fabric to complete the operation.

If you don't properly remove the node from the cluster, Service Fabric will assume that the nodes have simply failed and will return later after reporting them as having the status *Down*.

![Screenshot of the Service Fabric Cluster blade. Five nodes display with two of the nodes reporting a status of down.](../Linked_Image_Files\3.5.2_Scale_down.png)

Of course, you can also remove nodes using code.

#### Removing nodes from standalone clusters

Removing nodes is somewhat different from the process in Azure clusters. Instead of executing `Disable-ServiceFabricNode`, you execute the script `RemoveNode.ps1` on the server that you want to remove.

