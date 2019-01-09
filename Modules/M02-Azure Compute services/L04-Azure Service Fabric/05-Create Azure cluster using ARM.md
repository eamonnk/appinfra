

In this lesson, we'll deploy a Windows cluster that uses OMS for monitoring from the Azure Quickstart Templates gallery, found here: https://github.com/Azure/azure-quickstart-templates/tree/master/service-fabric-vmss-oms

![On the Microsoft Operations Management Suite desktop, the Overview - Security and Audit page displays.](../../Linked_Image_Files\3.2.2_OMS_cluster.png)

After filling in the requested details, a new Service Fabric cluster will be created. This process should take approximately 15 minutes. After it has completed, your resource group should look like this:

![The Resource group blade displays with a list of resources.](../../Linked_Image_Files\3.2.2_OMS_cluster_resource_grp.png)


- **Load balancer**

    Load balancers distribute (balance) traffic, or load, coming in from the outside world across master and agent nodes. Clients running outside the cluster take a DNS name, which gets resolved into an IP address. This is connected to the load balancer, which forwards incoming requests to healthy cluster nodes. This way, individual nodes may come and go without the client having to adapt for it.

    Unlike in ACS, there are no separate master and agent nodes in Service Fabric. All nodes contain services that define the cluster, and all nodes can run applications. The load balancer forwards traffic to individual nodes (NAT forwarding) or distributes it across all nodes (load balancing). 

- **Log analytics**

    This is a resource that is part of the OMS setup. It provides the capability to query logged diagnostics data.

- **Public IP address**

    IP addresses are used when computers need to communicate with each other across a network. A public IP address is a globally unique address, assigned to a single resource connected to the internet. A computer that has a public IP address that can be reached from anywhere across the world, by using the internet. The master public IP address is connected to the master load balancer to make it accessible across the internet, to manage the cluster.

- **Service Fabric cluster**

    This is a resource that provides an overview of your cluster. It shows information about cluster nodes, applications, active upgrades, security settings, and more.

- **Solution**

    Two OMS management solutions are added: 
    - Security and Audit

        This is an add-in for OMS that will scan the connected machines for known security vulnerabilities.
    - Service Fabric Analytics

        This is an add-in for OMS that will show relevant information about the health of your Service Fabric cluster. At this time, this solution is in Preview.

    >Learn more about OMS Management Solutions in Module 2, Chapter 2.4.

    >Learn more about Service Fabric Analytics in Module 3, Chapter 3.4.

- **Storage account**

    Azure Storage is Azure's cloud "storage as a service" platform. It offers services to store tables, blobs, queues, and files. There are two types of Azure Storage accounts, Standard and Premium. In this deployment, five Premium storage accounts are used to store the virtual hard disks of the virtual machines that are used. These are persisted as blobs. Azure Service Fabric is currently limited to 100 agents in a pool and a maximum of 20 virtual machines in one storage account. Premium storage is used for the best performance.

    There's another storage account, which is used to store diagnostics information coming from the nodes. In this deployment, OMS is configured to access data in this storage account to generate its dashboards from.

- **Virtual machine scale set**

    Often the load on applications you run on the cluster vary over time. For instance, more users are active during the day. It's likely to be cost effective to grow and shrink your cluster corresponding with the peaks and troughs in its use. It would be very time consuming to deploy and decommission nodes manually all the time. This process needs to be automated. 

    VM scale sets can help with that. They are templated virtual machines. It takes the definition of one VM and repeats the deployment as often as needed to create a set of identical VM's. A scale set can hold up to 1,000 nodes. This means that creating and resizing a big cluster is now very simple. It's a matter of changing the instance count and applying the change. A VM scale set is also implicitly an availability set, with five update domains and five fault domains.

    In an ASF cluster, it's possible to use multiple VM scale sets in one cluster. This way, you can optimize for costs even better. Applications that don't require large amounts of server resources can be placed on a scale set with smaller virtual machines, and applications that require more resources can be placed on larger virtual machines.

    >An important difference between ACS clusters and Service Fabric clusters is the fact that there are no master nodes in an Service Fabric cluster. The cluster management software runs on the same nodes as the applications do. This reduces complexity of the infrastructure, and usually, fewer resources need to be deployed to create an Service Fabric cluster.

- **Virtual network**

    All deployed machines need to be able to communicate securely. This is done by using software-defined networks. Machines in a virtual network are able to communicate with each other. Networks can be segmented into different subnets. Subnets are ranges of IP addresses in the network. Resources can be grouped into subnets to order them and to add security boundaries.