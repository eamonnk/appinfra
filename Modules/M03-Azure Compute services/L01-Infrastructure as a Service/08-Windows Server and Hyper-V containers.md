Windows Server and Windows 10 can create and run different types of containers and they each have different characteristics.

### Windows Server containers

The following diagram of high-level architecture shows how containers works on the Windows operating system. 

![This diagram has a Windows Kernel layer on the bottom. Above this a Host user mode box, and three Windows Server Containers.](../Linked_Image_Files\ContainersOnWindows.png)

As the diagram shows, the Windows operating system always has its default host user mode processes running Windows. On Windows, you now have additional services such as Docker and compute services that manage containers. 

When you start a new container, Docker talks to the compute services to create a new container based on an image. For each container, Docker will create a Windows container, each of which will require a set of system processes. These are always the same in every container. You then use your own application process to differentiate each container. These can be Microsoft Internet Information Services (IIS) or SQL Server processes that you run in the container.

On Windows Server 2016 and Windows Server 2019, you can run these containers so that they share the Windows kernel. This method is quite efficient, and the processes that run in the container will have no performance effect on the container because they access the kernel objects without indirect action. 

On Windows Server 2019, you can now run Windows and Linux containers alongside each other. 

### Hyper-V containers
When containers share the kernel and memory, it creates a slight chance that if a vulnerability occurs in the Windows operating system, an application might break out of its sandbox environment and inadvertently do something malicious. To avoid this, Windows provides a more secure alternative of running containers called *Hyper-V containers*.

The following diagram depicts the high-level architecture of Hyper-V containers on the Windows operating system. Hyper-V containers are supported on both Windows Server 2016 and newer versions, and on the Windows 10 Anniversary edition.

![This diagram has a Windows Kernel layer on the bottom. Above it is a Host User Mode box containing System process and Container Management boxes, and two VMs containing Hyper-V Containers and their contents.](../Linked_Image_Files\Hyper-v_ContainersOnWindows.png)


The main difference between Windows Server containers and Hyper-V containers is the isolation that the latter provides. Hyper-V containers are the only type of containers you can run on the Windows 10 operating system. Hyper-V containers have a small footprint and start fast compared to a full VM. You can run any image as a Hyper-V isolated container by using the **--isolation** option on the Docker command line, and specifying that the isolation be type **hyperv**. Refer to the following command for an example:

`docker run -it --isolation hyperv microsoft/windowsservercore cmd`

This command will run a new instance of a container based on the image `microsoft/windowsservercore`, and will run the command **cmd.exe** in interactive mode. 

###  Nano Server
*Nano Server* is the headless deployment option for Windows Server 2016 and Windows Server 2019, available via the semi-annual channel releases. It is specifically optimized for private clouds and datacenters and for running cloud-based applications. It is intended to be run as a container in a container host, such as a Server Core installation of Windows Server.

It's a remotely administered server operating system optimized for private clouds and datacenters. It's similar to Windows Server in Server Core mode, but it's significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. 

Nano Server also takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. Nano Server is ideal for a number of scenarios: 

- As a compute host for Hyper-V VMs, either in clusters or not. 
- As a storage host for Scale-Out File Server. 
- As a Domain Name System (DNS) server 
- As a web server running IIS 
- As a host for applications that are developed using cloud application patterns and run in a container or VM guest operating system 

