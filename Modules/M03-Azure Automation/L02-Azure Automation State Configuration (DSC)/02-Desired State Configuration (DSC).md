*Desired State Configuration* (DSC) is a configuration management approach that can be used for the configuration, deployment, and management of systems. DSC maintains your environments in a *defined state* that you specify, and ensures that they do not deviate from that state. Using DSC helps eliminate configuration drift and ensures *state* is maintained for compliance, security and performance purposes.

<a href="https://msdn.microsoft.com/en-us/powershell/dsc/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows PowerShell DSC</span></a> is a management platform in PowerShell that provides desired State. PowerShell DSC lets you manage, deploy, and enforce configurations for physical or virtual machines, including Windows and Linux machines.

### DSC Components

DSC consists of three primary components:
- *Configurations*. are declarative PowerShell scripts which define and configure instances of resources. Upon running the configuration, DSC (and the resources called by the configuration) set up your system in the state laid out by the configuration. DSC configurations are also idempotent: the *Local Configuration Manager* (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.
- *Resources*. contain the code that implements a configuration and maintains the specified state. Resources reside in PowerShell modules. Resources can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.
- *Local Configuration Manager (LCM)*. facilitates the interaction between resources and configurations. The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained. If the system is out of state, the LCM makes calls to the code in resources to bring the system into compliance with to the specified configuration.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc2.png" alt="Image showing three Pull Clients (Pull Client 1, 2, and 3) on the left. Each Pull Client has a box labeled 'Apply Configuration' and 'LCM'. Arrows labeled 'Get Configuration' point from each pull client to a Pull Server on the right. The Pull server has four boxes labeled 'DSC OData Endpoint', 'IIS Service', 'Configurations', and 'Resources'. Arrows labeled 'Send Configuration' point left from the Pull Server back to the three Pull Clients."></p>

> :information_source: For an overview of the basics of DSC, watch the TechEd 2014 event video [A Practical Overview of Desired State Configuration](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B417#fbid=).
