

*Desired State Configuration* (DSC) is a configuration management approach that you can use for configuration, deployment, and management of systems to ensure that an environment is maintained in a state that you specify (*defined state*), and doesn't deviate from that state. Using DSC helps eliminate configuration drift and ensures state is maintained for compliance, security, and performance purposes.

Windows PowerShell DSC is a management platform in PowerShell that provides desired State. PowerShell DSC lets you manage, deploy, and enforce configurations for physical or virtual machines, including Windows and Linux machines.

For more information, visit <a href="https://msdn.microsoft.com/en-us/powershell/dsc/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows PowerShell Desired State Configuration Overview</span></a>.

### DSC components
DSC consists of three primary components:

- Configurations. These are declarative PowerShell scripts that define and configure instances of resources. Upon running the configuration, DSC (and the resources being called by the configuration) will simply apply the configuration, ensuring that the system exists in the state laid out by the configuration. DSC configurations are also *idempotent*: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.
- Resources. They contain the code that puts and keeps the target of a configuration in the specified state. Resources reside in PowerShell modules and can be written to a model as something as generic as a file or a Windows process, or as specific as a Microsoft Internet Information Services (IIS) server or a VM running in Azure.
- Local Configuration Manager (LCM). The LCM runs on the nodes or machines you wish to configure. This is the engine by which DSC facilitates the interaction between resources and configurations. The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained. If the system is out of state, the LCM makes calls to the code in resources to apply the configuration according what has been defined

There are two methods of implementing DSC:
1. Push mode - Where a user actively applies a configuration to a target node, and the pushes out the configuration.
2. Pull mode - Where *pull clients* are configured to get their desired state configurations from a remote pull service automatically. This remote pull service is provided by a *pull server* which acts as a central control and manager for the configurations, ensures that nodes conform to the desired state and report back on their compliance status. The pull server can be set up as an SMB-based pull server or a HTTPS-based server. HTTPS based pull-server use the Open Data Protocol (OData) with the OData Web service to communicate using REST APIs. This is the model we are most interested in, as it can be centrally managed and controlled. The diagram below provides an outline of the workflow of DSC pull mode.


<p style="text-align:center;"><img src="../Linked_Image_Files/dsc2.png" alt="Three Pull Clients (Pull Client 1, 2, and 3), are on the left. Each Pull Client has a box labeled Apply Configuration, and LCM. Arrows labeled “Get Configuration” point from each pull client to a Pull Server on the right. The Pull server has four boxes: DSC OData Endpoint, IIS Service, Configurations, and Resources. Arrows labeled “Send Configuration” point left from the Pull Server back to the three Pull Clients."></p>



> **Note**: If you are not familiar with DSC, take some time to view <a href="https://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B417#fbid=" target="_blank"><span style="color: #0066cc;" color="#0066cc"> A Practical Overview of Desired State Configuration</span></a>. This is a great video from the TechEd 2014 event, and it covers the basics of DSC.
