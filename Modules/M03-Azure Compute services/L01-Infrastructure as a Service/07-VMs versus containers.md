
Containers are becoming increasingly popular depending on an organization's needs. This is because they offer numerous advantages over other environments such as VMs. The following are descriptions of some of these advantages. 

### Less resource intensive
Compared to running a VM, running a container requires relatively few resources. This is because the operating system is shared. When you start a VM you boot an entirely new operating system on top of the running operating system, and they share only the hardware. With containers, you share the memory, the disk, and the CPU. This means that the overhead associated with starting a container is quite low, and that the container also provides optimal isolation. 

### Fast startup
Because running a container requires only a few extra resources over the operating system, startup time is faster, and roughly equivalent to the time required to start a new process. The only additional items the OS needs to set up is the isolation for the process, which is done at the kernel level, and occurs quickly.   

### Improved server density
When you own hardware, you want to utilize that hardware as efficiently and cost-effectively as possible. With the introduction of VMs, sharing hardware among multiple VMs was introduced. 

Containers take this sharing concept one step further by enabling even more efficient utilization of memory, disk, and CPU from the available hardware. This is because VMs only consume the memory and CPU that they need. This results in fewer idle servers, resulting in better utilization of the existing compute resources. 

This is an especially important consideration for cloud providers. The higher the server density (the number of things that you can do with the hardware that you have), the more cost efficient the datacenter becomes. It's not surprising that containers are becoming more popular and that new tools for managing and maintaining containerized solutions are rapidly emerging.

### Density and isolation comparison
Containers allow for more density, scalability, and agility then VMs do, but they also enable more isolation than processes permit. The following diagram exhibits a comparison of density and isolation levels across the range of possible environments.

![This is a detailed description of the Density and Isolation levels diagram. From left to right, PC and VM are more isolated, while Container and Process are more efficient. Below, a table has the columns PC, VM, Container, and Process, and the rows Hardware, Kernel, and System Resources. A PC does not share any of these, a VM shares only Hardware, a Container shares hardware and kernel, and a Process shares all three. A note for the Container Kernel points out that Windows Hyper-V containers do not share a kernel.](../Linked_Image_Files\Density_and_Isolation.png)


### Windows vs. Linux containers
It is important to understand that containers are part of the operating system, and that each container shares the kernel of that operating system. This generally means that if you create an image on a machine running the Windows operating system, it is a Windows-specific image that needs a windows environment to run and vice versa.

There are tools native with Windows, such as **Windows Subsystem on Linux (WSL)** available in both *Windows 10* and *Windows Server 2019*, and **Docker for Windows**, which do allow you to run Linux and Windows containers side by side.
