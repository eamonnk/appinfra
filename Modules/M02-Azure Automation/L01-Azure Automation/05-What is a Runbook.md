
Runbooks serve as repositories for your custom scripts and workflows. They also typically reference Automation shared resources such as credentials, variables, connections, and certificates. 

Runbooks can contain other runbooks, thereby allowing you to build more complex workflows. You can invoke and run runbooks either on demand, or according to a schedule by leveraging Automation Schedule assets.

<p style="text-align:center;"><img src="../Linked_Image_Files/createarunbook.png" alt="Screenshot of the Add Runbook window. In the left pane, Quick Create: Create a new runbook is selected. In the right pane, the Runbook type drop down-box displays options such as PowerShell, Python 2, Graphical, and Other. Under Other is PowerShell Workflow, and Graphical PowerShell workflow."></p>

### Creating runbooks

When creating runbooks, you can either:

-  Create your own runbooks and import them. (For more information, see <a href="https://docs.microsoft.com/en-us/azure/automation/automation-creating-importing-runbook" target="_blank"><span style="color: #0066cc;" color="#0066cc">Creating or importing a runbook in Azure Automation</span></a>.) 
- Modify runbooks from the runbook gallery, which provides a rich ecosystem of runbooks available for your requirements. (Visit <a href="https://docs.microsoft.com/en-us/azure/automation/automation-runbook-gallery" target="_blank"><span style="color: #0066cc;" color="#0066cc">Runbook and module galleries for Azure Automation</span></a> for more information.)

There is also a vibrant open-source community creating runbooks that you can apply directly to your use cases. 

You can choose from different runbook types based on your requirements and Windows PowerShell experience. If you prefer to work directly with the PowerShell code, you can use a PowerShell runbook or a PowerShell Workflow runbook that you can edit offline or with the textual editor in the Azure portal. If you prefer to edit a runbook without being exposed to the underlying code, you can create a graphical runbook by using the graphical editor in the Azure portal.

### Graphical runbooks
Graphical and Graphical PowerShell Workflow runbooks are created and edited with the graphical editor in the Azure portal. You can export them to a file and then import them into another automation account, but you cannot create or edit them with another tool.

### PowerShell runbooks
PowerShell runbooks are based on Windows PowerShell. You edit the runbook code directly, using the text editor in the Azure portal. You can also use any offline text editor and then import the runbook into Azure Automation. PowerShell runbooks do not use parallel processing.

### PowerShell Workflow runbooks
These are text runbooks based on Windows PowerShell Workflow. You directly edit the code of the runbook using the text editor in the Azure portal. You can also use any offline text editor and import the runbook into Azure Automation. 

PowerShell workflow runbooks use parallel processing to allow for simultaneous completion of multiple tasks. Workflow runbooks take longer to start than PowerShell runbooks because it must be compiled prior to running.

### Python runbooks
Python runbooks compile under Python 2. You can directly edit the code of the runbook using the text editor in the Azure portal, or you can use any offline text editor and import the runbook into Azure Automation. 
You can also utilize Python libraries. However, only Python 2 is supported at this time. To utilize third-party libraries, you must first import the package into the Automation Account.


> **Note**: You can't convert runbooks from graphical to textual type, or vice-versa.

For more information on the different types of runbooks, see <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-runbook-types" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Automation runbook types</span></a>.


