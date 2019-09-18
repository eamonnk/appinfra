
*Azure Automation State configuration DSC* is an Azure cloud-based implementation of PowerShell DSC, available as part of Azure Automation. Azure Automation State configuration allows you to write, manage, and compile PowerShell DSC configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud.


### Why use Azure Automation DSC
The following outlines some of the reasons why we would consider using Azure Automation DSC:
- Built-in pull server. Provides a DSC pull server similar to the Windows Feature DSC-service so that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in pull server in Azure Automation eliminates the need to set up and maintain your own pull server.
- Management of all your DSC artifacts. From either the Azure portal or PowerShell, you can manage all your DSC configurations, resources, and target nodes.
- Import reporting data into Log Analytics. Nodes that are managed with Azure Automation state configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation state configuration to send this data to your Log Analytics workspace. 


### How Azure Automation state configuration works
The general process for how Azure Automation State configuration works is as follows:

1.  Create a PowerShell script with the configuration element

2.  Upload the script to Azure Automation and compile the script into a MOF file. The file is transferred to the DSC pull server, which is provided as part of the Azure Automation service. (See <a href="https://msdn.microsoft.com/en-us/library/aa823192(v=vs.85).aspx" target="_blank"><span style="color: #0066cc;" color="#0066cc">Managed Object Format (MOF) file</span></a> for more information on MOF files.)

3.  Define the nodes that will use the configuration, and then apply the configuration.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc1.png" alt="A diagram is made up of three sections: Configurations, Node Configurations, and Nodes. On the left,  Configurations has a code window with text beneath that says “1 or more per automation account.” An arrow labeled “Compiled, put on pull server (via compilation jobs)” points from section one to section 2, Node Configurations (.MOF configuration documents). This section has three Sharepoint.WebService icons. Text below the icons says “1 or more per Configuration.” An arrow labeled “Applied (via node pulls)” points from section 2 to section 3, Nodes, which has six Node icons, with the text “1 or more per Node Configuration&quot beneath it."></p>
