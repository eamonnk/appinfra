### How Containers Work on Windows

The following diagram of high-level architecture shows how Docker works on Windows.

![This diagram has a Windows Kernel layer on the bottom. Above this are the following boxes: Host user mode, and three Windows Server Containers.](../Linked_Image_Files\ContainersOnWindows.png)

You can see that Windows always has its default host user mode processes that run Windows. On Windows, you now have additional services such as Docker engine and compute services that handle containers.

When you start a new container, the Docker engine talks to the compute services to spin up a new container based on an image. For each container, the Docker engine will create a Windows container. Each container needs a set of system processes that are always the same in every container. You then use your own application process to differentiate each container. These can be IIS or SQL Server processes that you run in the container.

On Windows Server 2016 and 2019 Nano server, you can run these containers so that they share the Windows kernel. This is very efficient, and the processes that run in the container will have no performance effect on running in the container because they access the kernel objects without further indirection. They also share the memory. Thus, there is a slight chance that if a vulnerability occurs in the Windows operating system, an application might break out of its sandboxed environment and do something malicious. To avoid this, Windows provides a more secure alternative of running containers called Hyper-V containers.

On Windows Server 2019 nano server, you can now run Windows and Linux containers alongside each other in Hyper-V. Also, Windows Server 2019 Nano Server has been optimized for .NET Core applications to allow for the running of .NET Core based applications

### Hyper-V containers
The following diagram depicts the high-level architecture of Hyper-V containers on Windows. Hyper-V containers are supported on both Windows Server 2016 and newer versions, and on the Windows 10 Anniversary edition.

![This diagram has a Windows Kernel layer on the bottom. Above this are the following  three boxes: Host User Mode with System process and and Container Management boxes, and two Virtual Machines with Hyper-V Containers and their contents.](../Linked_Image_Files\Hyper-v_ContainersOnWindows.png)


The main difference between containers and Hyper-V containers is the isolation that the latter provides. Hyper-V containers are the only type of containers you can run on Windows 10. Hyper-V containers do have a small footprint and start fast compared to a full virtual machine. You can run any image as a Hyper-V isolated container by using the `--isolation` option on the Docker command line and specifying that the isolation be type **hyperv**.


`docker run -it --isolation hyperv microsoft/windowsservercore cmd`

This will run a new instance of a container based on the image `microsoft/windowsservercore` and will run the command `cmd.exe` in interactive mode.

### Windows Server 2016 and 2019 Nano Server
Nano Server is the headless deployment option for Windows Server 2016, 2019 and later versions. It is a remotely administered server operating system optimized for private clouds and datacenters. It is similar to Windows Server in Server Core mode, but significantly smaller, has no local logon capability, and only supports 64-bit applications, tools, and agents. It takes up far less disk space, sets up significantly faster, and requires far fewer updates and restarts than Windows Server. When it does restart, it restarts much faster. The Nano Server installation option is available for Standard and Datacenter editions of Windows Server 2016.
Nano Server is ideal for a number of scenarios:
- As a "compute" host for Hyper-V virtual machines, either in clusters or not
- As a storage host for Scale-Out File Server.
- As a DNS server
- As a web server running Internet Information Services (IIS)
- As a host for applications that are developed using cloud application patterns and run in a container or virtual machine guest operating system
