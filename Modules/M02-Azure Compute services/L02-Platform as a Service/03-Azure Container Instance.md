

Azure Container Instances consist of a PaaS service that was recently added to Microsoft Azure. It offers the capability to run both Linux and Windows containers. By default, it runs single containers, which means that individual containers are isolated from each other and cannot interact with each other. The isolation between individual containers is achieved by using Hyper-V containers. This gives you the same level of protection as using a virtual machine would, by running your container inside a small utility VM. You specify the amount of memory in gigabytes for each container, and the count of processors (CPUs) to assign. Furthermore, containers are billed per second. This means that you are in complete control, and that you don’t pay for resources you don’t need.

By assigning a public IP address to your container, you make it accessible from the outside world. If you look at the image below, you can see a container that exposes port 80. The port is connected to a public IP address that accepts traffic at port 80 of the virtual host. Note that in ACI, port mappings are not available, so the same port number must be used by both the container and container host.

>It is possible to run both long-running processes and task-based containers. This is controlled by the container restart policy.

### No more VM management

It is important to know that with ACI you don’t need to own a virtual machine to run your containers. This means that you don’t need to worry about creating, managing, and scaling them. In the picture below, both the network and the virtual machine, the container host, are completely managed for you, and you have no control over either of them. 

![Nested boxes display in the following order, from outside to inside: Virtual Network, Container Host (VM), and Container with Web server on Port 80.](../../Linked_Image_Files\2.2.8.Container-Instance.png)

### Container groups
By default, your containers are isolated from each other. But what if you need interaction between containers? To support this kind of scenario, there is the concept of container groups. Containers inside a container group are deployed on the same machine, and they use the same network. They also share their lifecycle: all containers in the group are started and stopped together.

>At this time, container groups cannot be updated. To change an existing group, you need to delete and recreate it.

Containers are always part of a container group. Even if you deploy a single container, it will be placed into a new group automatically. When using Windows containers, a group can have only one container. This is because network namespaces are not available on Windows.

![As in the previous image, the Virtual Network, Container Host, and Container group boxes are nested. This time, within the container group are the following containers: Logging (Port 8080), Job processing (Port 8000), and Job Generator (Port 80). Outside of the boxes are Azure file Share and Service bus, which have arrows pointing to and from the containers.](../../Linked_Image_Files\2.2.8.Container-Group.png)