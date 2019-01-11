

*Desired State Configuration* is a configuration management approach that can be used for configuration, deployment, and management of systems to ensure an evironment is maintained in a *defined state* that you specify, and doesn't deviate from that state. Using DSC helps eliminate configuration drift and ensures *state* is maintained for compliance, security and performance purposes.

<a href="https://msdn.microsoft.com/en-us/powershell/dsc/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows PowerShell DSC</span></a> is a management platform in PowerShell that provides desired State. PowerShell DSC lets you manage, deploy, and enforce configurations for physical or virtual machines, including Windows and Linux machines.

### DSC Components
DSC consists of three primary components:
- **Configurations** -  are declarative PowerShell scripts which define and configure instances of resources. Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration. DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.
- **Resources** - are the "make it so" part of DSC. They contain the code that put and keep the target of a configuration in the specified state. Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.
- **Local Configuration Manager (LCM)** -  is the engine by which DSC facilitates the interaction between resources and configurations. The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained. If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc2.png" alt="Three Pull Clients (Pull Client 1, 2, and 3), are on the left. Each Pull Client has a box labeled Apply Configuration and LCM. Arrows labeled “Get Configuration” point from each pull client to a Pull Server on the right. The Pull server has four boxes labeled DSC OData Endpoint, IIS Service, Configurations, and Resources. Arrows labeled “Send Configuration” point left from the Pull Server back to the three Pull Clients."></p>



> **Note**: If you are not familiar with DSC, take some time to view <a href="https://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B417#fbid=" target="_blank"><span style="color: #0066cc;" color="#0066cc"> A Practical Overview of Desired State Configuration</span></a>. This is a great video from the TechEd 2014 event, and it covers the basics of DSC.
