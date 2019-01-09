
Containers are becoming increasingly popular because they offer numerous advantages over other environments such as virtual machines, depending on an organization's needs. Following are descriptions of some of those advantages. 

### Less resource intensive
Compared to running a virtual machine, running a container requires relatively few resources. This is because the operating system is shared. When you start a virtual machine, you boot a whole new operating system on top of the running operating system, and you only share the hardware. With containers, you share the memory, the disk, and the CPU. This means that the overhead associated with starting a container is very low, and that the container also provides optimal isolation. 

### Fast startup
Because running a container requires only a few extra resources of the operating system, startup time is very fast, roughly equivalent to the time required to start a new process. The only additional thing the OS needs to set up is the isolation of the process, which is done at the kernel level and is very fast.   

### Improved server density
When you own hardware, you want to utilize that hardware as efficiently and cost-effectively as possible. With the introduction of virtual machines, we made a first step in this direction by enabling sharing of hardware among multiple virtual machines. 

Containers take this sharing concept one step further, enabling us to utilize the memory, disk, and CPU of available hardware even more efficiently because we only consume the memory and CPU that we need. This results in fewer idle running servers, hence better utilization of the compute resources that we have. 

This is an especially important consideration for cloud providers. The higher the server density (the number of things that you can do with the hardware that you have) the more cost efficient the datacenter becomes. So it is not surprising that containers are receiving a lot of attention and that new tools for managing and maintaining containerized solutions are emerging rapidly.

### Density and Isolation Comparison
Containers allow for more density, scalability, and agility then virtual machines do, but enable more isolation than processes permit. The diagram below shows a comparison of density and isolation levels across the range of possible environments.


![This is a detailed description of the Density and Isolation levels diagram. From left to right, PC and VM are more isolated, while Container and Process are more efficient. Below, a table has the columns PC, VM, Container, and Process, with rows Hardware, Kernel, and System Resources (such as File System). A PC does not share any of these, a VM shares only Hardware, a Container shares hardware and kernel, and a Process shares all three. A note for the Container Kernel points out that Windows Hyper-V containers do not share a kernel.](../../Linked_Image_Files\Density_and_Isolation.png)


### Windows vs. Linux Containers
It is important to understand that containers are part of the operating system and that each container shares the kernel of that operating system. This means that if you create an image on a Windows machine, it is a Windows specific image which can only be run on a Windows operating system. Consequently, a Linux container cannot run on a Windows operating system and vice versa.