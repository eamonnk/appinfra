
Azure Automation supports source control integration that enables you to keep your runbooks in your Automation account up to date with your scripts in your GitHub or Azure DevOps source control repository. 

Source control allows you to more easily collaborate with your team, track changes, and roll back to earlier versions of your runbooks. For example, source control allows you to sync different branches in source control to your development, test, or production Automation accounts. This makes it easier to promote code you've tested in your development environment to your production Automation account.

Azure Automation supports three types of source control:

- GitHub
- Azure DevOps (Git)
- Azure DevOps (TFVC)

Source control allows you to push code from Azure Automation to source control, or pull your runbooks from source control to Azure Automation. Source control sync jobs run under the user's Automation Account and are billed at the same rate as other Automation jobs.


### Integrate source control with Azure Automation

You integrate source control with Azure Automation using the following steps:

1. In the Azure Portal, access your Automation account.
2. Under Account Settings, select **Source control**, and then select **+ Add**.
3. In the **Source Control Summary** blade, select **GitHub** as source control type, and then select **Authenticate**.

    > Note: You will require a GitHub account to complete the next step.

4. When the browser page opens prompting you to authenticate to https://www.github.com, select **Authorize azureautomation** and enter your GitHub account password.

    If successful you should receive an email notification from GitHub stating that *A third-party OAuth Application (Automation Source Control) with repo scope was recently authorized to access your account.*

5. After authentication completes, fill in the details based on the following table, and then select **Save**.

    | Property | Description |
    | --- | --- |
    | Name| Friendly name |
    | Source control type | GitHub, Azure DevOps Git or Azure Devops TFVC |
    | Repository |The name of the repository or project |
    | Branch | The branch from which to pull the source files. Branch targeting is not available for the TFVC source control type|
    | Folder Path | The folder that contains the runbooks to sync.|
    | Auto sync | Turns on or off automatic sync when a commit is made in the source control repository |
    | Publish Runbook| If set to **On**, after runbooks are synced from source control they will be automatically published |
    | Description | A text field to provide additional details |
    
6. If you set **Autosync** to **Yes**,  a full sync will start. If you set **Auto sync** to **No**, open the **Source Control Summary** blade again by selecting your repository in Azure Automation, and then selecting **Start Sync**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/sourcecontrolsummary.png" alt="Screenshot of the Source Control Summary blade containing fields and details to be filled in."></p>

7. Verify that your source control is listed in the **Azure Automation Source control** page for you to use.

    <p style="text-align:center;"><img src="../Linked_Image_Files/sourcecontrol2.png" alt="Screenshot of the Azure Automation source control window with the just-created source control account."></p>


