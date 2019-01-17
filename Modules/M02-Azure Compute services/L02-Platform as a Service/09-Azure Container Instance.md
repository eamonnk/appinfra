

*Azure Container Instances* is a PaaS service on Microsoft Azure. It offers the capability to run both Linux and Windows containers. By default, it runs single containers, which means that individual containers are isolated from each other and cannot interact with each other.

*Azure Container Instances* offers the fastest and simplest way to run a container in Azure, without having to provision any virtual machines and without having to adopt a higher-level service.


![Nested boxes display in the following order, from outside to inside: Virtual Network, Container Host (VM), and Container with Web server on Port 80.](../Linked_Image_Files\2.2.8.Container-Instance.png)

### No more VM management

It is important to know that with ACI you don’t need to own a virtual machine to run your containers. This means that you don’t need to worry about creating, managing, and scaling them. In the picture below, both the network and the virtual machine, the container host, are completely managed for you, and you have no control over either of them.

### Hypervisor-level security
Historically, containers have offered application dependency isolation and resource governance but have not been considered sufficiently hardened for hostile multi-tenant usage. Azure Container Instances guarantees your application is as isolated in a container as it would be in a VM.

The isolation between individual containers is achieved by using Hyper-V containers. This gives you the same level of protection as using a virtual machine would, by running your container inside a small utility VM.


### Public IP connectivity and DNS name
Azure Container Instances enables exposing your containers directly to the internet with an IP address and a fully qualified domain name (FQDN). When you create a container instance, you can specify a custom DNS name label so your application is reachable at `customlabel.azureregion.azurecontainer.io`.

By assigning a public IP address to your container, you make it accessible from the outside world. If a container that exposes port 80, as in the image above, the port is connected to a public IP address that accepts traffic at port 80 of the virtual host.

> **Note**: Port mappings are not available in ACI, so the same port number must be used by both the container and container host.


### Custom sizes and Resources
Containers are typically optimized to run just a single application, but the exact needs of those applications can differ greatly. Azure Container Instances provides optimum utilization by allowing exact specifications of CPU cores and memory.

You specify the amount of memory in gigabytes for each container, and the count of processors (CPUs) to assign. For compute-intensive jobs such as machine learning, Azure Container Instances can schedule Linux containers to use NVIDIA Tesla GPU resources (preview).

You pay based on what you need and get billed by the second, so you can fine-tune your spending based on actual need and  don’t pay for resources you don’t need.

### Virtual network deployment (preview)
Currently in preview, this feature of Azure Container Instances enables deployment of container instances into an Azure virtual network. By deploying container instances into a subnet within your virtual network, they can communicate securely with other resources in the virtual network, including those that are on premises (through VPN gateway or ExpressRoute).


### Persistent storage
To retrieve and persist state with Azure Container Instances, it is possible to use Azure Files shares.

It is possible to run both long-running processes and task-based containers. This is controlled by the container restart policy.


### Container groups
By default, containers are isolated from each other. But what if interaction between containers is needed? To support this kind of scenario, there is the concept of container groups. Containers inside a container group are deployed on the same machine, and they use the same network. They also share their lifecycle: all containers in the group are started and stopped together.


Containers are always part of a container group. Even if you deploy a single container, it will be placed into a new group automatically. When using Windows containers, a group can have only one container. This is because network namespaces are not available on Windows.

![As in the previous image, the Virtual Network, Container Host, and Container group boxes are nested. This time, within the container group are the following containers: Logging (Port 8080), Job processing (Port 8000), and Job Generator (Port 80). Outside of the boxes are Azure file Share and Service bus, which have arrows pointing to and from the containers.](../Linked_Image_Files\2.2.8.Container-Group.png)


### Usage Scenario

*Azure Container Instances*  is a recommended compute option for any scenario that can operate in isolated containers, including simple applications, task automation, and build jobs. For scenarios where you need full container orchestration, including service discovery across multiple containers, automatic scaling, and coordinated application upgrades, we recommend Azure Kubernetes Service (AKS).
