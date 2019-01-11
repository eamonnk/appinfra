
*Azure Automation State configuration DSC* is an Azure cloud-based implementation of PowerShell DSC, available as part of **Azure Automation**.


*Azure Automation State configuration* allows you to write, manage, and compile PowerShell Desired State Configuration (DSC) configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud.


### Why use Azure Automation DSC

- *Built-in pull server* - provides a DSC pull server similar to the Windows Feature DSC-Service so that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in pull server in Azure Automation eliminates the need to set up and maintain your own pull server.

- *Management of all your DSC artifacts* - From the Azure portal, or from PowerShell, you can manage all your DSC configurations, resources, and target nodes.

- *Import reporting data into Log Analytics* - Nodes that are managed with Azure Automation State Configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation State Configuration to send this data to your Log Analytics workspace. 



### How Azure Automation State configuration works
The general process for how Azure Automation State configuration works is as follows, and outlined in the screenshot below:

1.  *Confugurations* - Create a Windows PowerShell script with the configuration element

2.  *Node Configurations* - Upload the script to Azure Automation and compile the script into a <a href="https://msdn.microsoft.com/en-us/library/aa823192(v=vs.85).aspx" target="_blank"><span style="color: #0066cc;" color="#0066cc">Managed Object Format (MOF) file</span></a>. The file is transferred to the DSC pull server. This is provided as part of the Azure Automation service.

3.  *Nodes* - Define the nodes that will use the configuration and apply the configuration.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc1.png" alt="This screenshot is made up of three sections. Section 1 is Configurations. Section 2 is Node Configurations, and Section 3 is Nodes. On the left, 1: Configurations has a code window with text beneath that says “1 or more per automation account.” An arrow labeled “Compiled, put on pull server (via compilation jobs)” points from section one to section 2. In the middle, 2: Node Configurations (.MOF configuration documents) has three Sharepoint.WebService icons. Text below the icons says “1 or more per Configuration.” An arrow labeled “Applied (via node pulls)” points from section 2 to section 3. On the right, 3: Nodes has six Node icons, with the text “1 or more per Node Configuration."></p>