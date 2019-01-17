*Runbooks* serve as repositories for your custom scripts and workflows. In addition, runbooks typically reference Azure Automation Shared Resources, such as credentials, variables, connections, and certificates.

Runbooks, can also can contain other runbooks, thereby allowing you to build up complex workflows. You can invoke and run runbooks either on demand or according to your chosen schedule by leveraging Automation Schedule assets.

### Creating runbooks

With Azure Automation the following options are possible.

- You can [create your own runbooks](https://docs.microsoft.com/en-us/azure/automation/automation-creating-importing-runbook) and import them.
- The [Runbook Gallery](https://docs.microsoft.com/en-us/azure/automation/automation-runbook-gallery) contains runbooks created by Microsoft. You can modify these runbooks to suit your requirements and import them.

<p style="text-align:center;"><img src="../Linked_Image_Files/createarunbook.png" alt="Screenshot of the Add Runbook window. In the left pane, the 'Quick Create: Create a new runbook option' is highlighted. In the right pane, a drop down box is highlighted. The dropdown menu contains available runbook type options. The available runbook type options shown are: PowerShell, Python 2, Graphical, PowerShell Workflow and Graphical PowerShell workflow."></p>

There is also a vibrant open-source community creating runbooks that you may apply to your use cases.

### Runbook types

You can choose from five different [runbook types](https://azure.microsoft.com/en-us/documentation/articles/automation-runbook-types), according to your requirements and Windows PowerShell experience.

If you prefer working with PowerShell code directly, you can use PowerShell or PowerShell Workflow runbooks. These *Textual type runbooks* can be edited offline, with a text editor, or with the online text editor in Azure portal. If you prefer to not work with the underlying code, you can create *Graphical type runbooks* using the graphical editor in the Azure portal.

- *Graphical runbooks*. Graphical and Graphical PowerShell Workflow runbooks are created and edited with the graphical editor in the Azure portal. You can export them to a file and then import them into another automation account, but you *cannot* create or edit them with another tool.

- *PowerShell runbooks*. Based on Windows PowerShell. You directly edit the code of the runbook using the text editor in the Azure portal. You can also use any offline text editor and import the runbook into Azure Automation. PowerShell runbooks do not use parallel processing.

- *PowerShell Workflow runbooks*. Text runbooks based on *Windows PowerShell Workflow*. You directly edit the code of the runbook using the text editor in the Azure portal. You can also use any offline text editor and import the runbook into Azure Automation. PowerShell workflow runbooks use parallel processing to allow completion of multiple tasks at the same time. Workflow runbooks take longer to start than PowerShell runbooks since it needs to be compiled before running

- *Python runbooks*. Python runbooks compile under Python 2. You can directly edit the code of the runbook using the text editor in the Azure portal, or you can use any offline text editor and import the runbook into Azure Automation. You can Utilize the robust Python libraries. Only Python 2 is supported at the moment. To utilize third-party libraries, you must import the package into the Automation Account for it to be used.

> :information_source: Graphical type runbooks refer to Graphical and Graphical PowerShell Workflow runbooks. Graphical type runbooks are created and edited with the online graphical editor in Azure portal.
>
>Textual type runbooks are PowerShell, Windows PowerShell Workflow, and Python runbooks. Textual type runbooks are created and edited with the online text editor in Azure portal, or with an offline text editor.
>
>You cannot convert a Graphical type runbook to a Textual type runbook, or vice-versa.
