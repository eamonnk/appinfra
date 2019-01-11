
*Runbooks* deliver serve as repositories for your custom scripts and workflows. In addition, runbooks typically reference Automation shared resources, such as credentials, variables, connections, and certificates. 

Runbooks, can also can contain other runbooks, thereby allowing you to build more complex workflows. You can invoke and run runbooks either on demand or according to your chosen schedule by leveraging Automation Schedule assets.

<p style="text-align:center;"><img src="../Linked_Image_Files/createarunbook.png" alt="Screenshot of the Add Runbook window. In the left pane, the Quick Create: Create a new runbook option is selected. In the right pane, pane displays a drop down box containing runbook type options such as PowerShell, Python 2, Graphical, PowerShell Workflow and Graphical PowerShell workflow."></p>

### Creating runbooks
-  You can <a href="https://docs.microsoft.com/en-us/azure/automation/automation-creating-importing-runbook" target="_blank"><span style="color: #0066cc;" color="#0066cc">create your own runbooks</span></a> from scratch and import them
- Modify runbooks from the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-runbook-gallery" target="_blank"><span style="color: #0066cc;" color="#0066cc">Runbook Gallery</span></a>, where there is a rich ecosystem of runbooks available, for your own requirements. 

There is also a vibrant open-source community creating runbooks that you can use to directly apply to your use cases. 

You can choose from **five** different <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-runbook-types" target="_blank"><span style="color: #0066cc;" color="#0066cc">runbook types</span></a> based on your requirements and Windows PowerShell experience.

 If you prefer to work directly with the PowerShell code, you can use a PowerShell runbook or a PowerShell Workflow runbook that you can edit offline or with the textual editor in the Azure portal. If you prefer to edit a runbook without being exposed to the underlying code, you can create a graphical runbook by using the graphical editor in the Azure portal.

### Graphical runbooks
Graphical and Graphical PowerShell Workflow runbooks are created and edited with the graphical editor in the Azure portal. You can export them to a file and then import them into another automation account, but you **cannot** create or edit them with another tool.

### PowerShell runbooks
Based on Windows PowerShell. You directly edit the code of the runbook using the text editor in the Azure portal. You can also use any offline text editor and import the runbook into Azure Automation. Powershell runbooks do not use parallel processing. 

### PowerShell Workflow runbooks
Text runbooks based on **Windows PowerShell Workflow**. You directly edit the code of the runbook using the text editor in the Azure portal. You can also use any offline text editor and import the runbook into Azure Automation. PowerShell workflow runbooks use parallel processing to allow completion of multiple tasks at the same time. Workflow runbooks take longer to start than PowerShell runbooks since it needs to be compiled before running

### Python runbooks
Python runbooks compile under Python 2. You can directly edit the code of the runbook using the text editor in the Azure portal, or you can use any offline text editor and import the runbook into Azure Automation. You can Utilize the robust Python libraries. Only Python 2 is supported at the moment. To utilize third-party libraries, you must import the package into the Automation Account for it to be used.


> **Note**: You can't convert runbooks from graphical to textual type or vice-versa.


