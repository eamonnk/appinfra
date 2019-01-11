

Azure Automation supports source control integration to allow you to keep your runbooks in your Automation account up-to-date with your scripts in your GitHub or Azure DevOps source control repository. 

Source control allows you to easily collaborate with your team, track changes, and roll back to earlier versions of your runbooks. For example, source control allows you to sync different branches in source control to your development, test, or production Automation accounts, making it easy to promote code that has been tested in your development environment to your production Automation account.

Azure Automation supports 3 types of source control:
- GitHub
- Azure DevOps (Git)
- Azure DevOps (TFVC)

Source control allows you to push code from Azure Automation to source control **or** pull your runbooks from source control to Azure Automation. Source control sync jobs run under the users Automation Account and are billed at the same rate as other Automation jobs.

Azure source control PowerShell Workflow, PowerShell Scripts, DSC Configurations, Graphical, and Python 2.

### Integrate Source control with Azure Automation
You integrate source control with Azure Automation as follows:

1. In the **Azure Portal** and your Automation account
2. Under **Account Settings** click on **Source control** then click **+ Add**
3. In the Source Control Summary pane select **GitHub** as source control type and then click **Authenticate**
4. A browser page opens and you are prompted to authenticate to https://www.github.com ( you need a github account to be able to complete this step), click **Authorize azureautomation** in the browser and enter your Github account password.

    If successful you should receive email notification from github stating that *A third-party OAuth Application (Automation Source Control) with repo scope was recently authorized to access your account.*

5. Once Authenticated, fill in the details based on the table below.

    | Property | Description |
    | --- | --- |
    | name| friendly name |
    | source control type | GitHub, Azure DevOps Git or Azure Devops TFVC |
    | Repository |The name of the repository or project |
    | Branch | The branch to pull the source files from. Branch targeting is not available for the TFVC source control type|
    | Folder Path|The folder that contains the runbooks to sync.|
    | Auto sync | Turns on or off automatic sync when a commit is made in the source control repository |
    | Publish Runbook| If set to On, after runbooks are synced from source control they will be automatically published |
    | Description | A text field to provide additional details |
    
6. Click Save. If **Autosync** was set to **Yes**,  a full sync will then be started. If you set **Auto sync** to **No**, you can open the Source Control summary blade again, by clicking on your repo in Azure Automation, and selecting **Start Sync**

<p style="text-align:center;"><img src="../Linked_Image_Files/sourcecontrolsummary.png" alt="Screenshot of the source control summary pane containing fields and details to be filled in."></p>

7. Once created it is then listed in the **Azure Automation Source control** page for you to use.

<p style="text-align:center;"><img src="../Linked_Image_Files/sourcecontrol2.png" alt="Screenshot of the source control summary pane containing fields and details to be filled in."></p>


