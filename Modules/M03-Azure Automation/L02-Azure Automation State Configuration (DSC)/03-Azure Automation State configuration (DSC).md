*Azure Automation State configuration* is an Azure, cloud-based implementation of PowerShell DSC which is available as part of Azure Automation. Azure Automation State configuration allows you to write, manage, and compile PowerShell Desired State Configuration (DSC) configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud.

### Azure Automation State configuration features

- *Built-in pull server*. provides a DSC pull server similar to the Windows Feature DSC-Service so that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in pull server in Azure Automation eliminates the need to set up and maintain your own pull server.

- *Management of all your DSC artifacts*. From the Azure portal, or from PowerShell, you can manage all your DSC configurations, resources, and target nodes.

- *Import reporting data into Log Analytics*. Nodes that are managed with Azure Automation State Configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation State Configuration to send this data to your Log Analytics workspace.

### How Azure Automation State configuration works

The following describes the general process for how Azure Automation State configuration works.

1. *Configurations*. Create a Windows PowerShell script with the **Configuration element**.

2. *Node Configurations*. Upload the script to Azure Automation and compile the script into a [Managed Object Format (MOF) file](https://msdn.microsoft.com/en-us/library/aa823192(v=vs.85).aspx). The file is transferred to the DSC pull server. This is provided as part of the Azure Automation service.

3. *Nodes*. Define the nodes that will use the configuration and apply the configuration.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc1.png" alt="Image made up of three sections. Section 1 is labeled 'Configurations'. Section 2 is labeled 'Node Configurations'. Section 3 is labeled 'Nodes'. On the left, below the Configurations label is an screenshot of a text editor that contains code. Text below the text editor image state '1 or more per automation account'. An arrow labeled 'Compiled, put on pull server (via compilation jobs)'' points from section 1 to section 2. In the middle, below the section 2 label, there are three squares that represent the .MOF node configuration documents). Text below the icons states '1 or more per Configuration'. An arrow labeled 'Applied (via node pulls)'' points from section 2 to section 3. On the right, below the 'Nodes' label, there  are has six icons representing six nodes. Text below the icons states '1 or more per Node Configuration'."></p>

> :information_source: The following summarizes the main features of Azure Automation State configuration.
>
> - The *built-in pull server* eliminates the need to set up and maintain your own pull server.
> - Provides *centralized management of DSC artifacts* in Azure portal or PowerShell.
> - *Enhances reporting and analyzes capabilities* by capturing detailed status data from managed nodes, for importing into Log Analytics via the built-in pull server.
