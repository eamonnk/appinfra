
To [write the workflow](https://azure.microsoft.com/en-us/documentation/articles/automation-first-runbook-textual/), use a script editor, such as the Windows PowerShell Integrated Scripting Environment (ISE), which enforces workflow syntax and highlights syntax errors.

A benefit of using thePowerShell IDE is that it auto compiles your code and allows you to save the artifact. The syntactic differences between scripts and workflows are significant, so a tool that knows workflows, as well as scripts, will save you significant coding and testing time.

### Syntax
Begin with the **workflow** keyword, which identifies a workflow command to Windows PowerShell. The **workflow** keyword is required in a script workflow. The name of the workflow follows the **workflow** keyword. The body of the workflow is enclosed in braces. A workflow is a Windows PowerShell command type. Select a name with a verb-noun format.

```PowerShell
        workflow Test-Workflow
        
        {
           ...
        }
```

To add parameters to a workflow, use the **Param** keyword. These are the same techniques that you use to add parameters to a function. Lastly, simply add your standard PowerShell commands.

```powershell
    workflow MyFirstRunbook-Workflow*
    
    {
    Param(
        [string]$VMName,
        [string]$ResourceGroupName
        )
        ....
        Start-AzureRmVM -Name $VMName -ResourceGroupName $ResourceGroupName
    }
```
### Create a new runbook
1. In the **Azure portal**, open your Automation account.
2. Click **Runbooks** under **Process Automation** to open the list of runbooks
3. Create a new runbook by clicking on the **+ Add a runbook** button and then select **Create a new runbook**.
4. Give the runbook the name **MyFirstRunbook-Workflow.**
5. In this case, you're going to create a **PowerShell Workflow** runbook so select **Powershell Workflow** for **Runbook type**.
6. Click **Create** to create the runbook and open the textual editor.

#### Add Code to a runbook
You can either type code directly into the runbook, or you can select cmdlets, runbooks, and assets from the Library control and have them added to the runbook with any related parameters. For this walkthrough, you type directly into the runbook.

1. Type Write-Output "Hello World." between the braces, so it looks like the below

    ```Powershell
    Workflow MyFirstRunbook-Workflow
    {
    Write-Output "Hello World"
    }
    ```
2. Save the runbook by clicking Save

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1.png" alt="Screenshot of workflow editor containing cmdlets, runbooks and assets on the lefthand side and the sample code on the right for hello world sample."></p>

#### Test the runbook
Before you publish the runbook to make it available in production, you want to test it to make sure that it works properly. When you test a runbook, you run its Draft version and view its output interactively.
1. Click the Test pane

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1.png" alt="Screenshot of workflow editor highlighting Test Pane button."></p>

2. Click **Start** to start the test. This should be the only enabled option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow2.png" alt="Screenshot of the test pane highlighting the start button."></p>

3. A runbook job is created and its status displayed. The job status will start as Queued indicating that it is waiting for a runbook worker in the cloud to come available. It moves to Starting when a worker claims the job, and then Running when the runbook actually starts running. 
    
4. When the runbook job completes, its output is displayed. In your case, you should see Hello World. Close the **Test pane** when finished

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow3.png" alt="Screenshot of the test pane with the runbok test complete displaying the output Hello World."></p>

#### Publish and run the runbook
The runbook that you created is still in Draft mode. You need to publish it before you can run it in production. When you publish a runbook, you overwrite the existing Published version with the Draft version. In your case, you don't have a Published version yet because you just created the runbook.

1. In the runbook editor click **Publish** to publish the runbook and then **Yes** when prompted.
2. If you scroll left to view the runbook in the Runbooks pane now, it shows an **Authoring Status** of **Published**.
3. Scroll back to the right to view the pane for **MyFirstRunbook-Workflow**. The options across the top allow us to start, view, edit, link to schedule to start at some time in the future, add a webhook, delete or export.
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow4.png" alt="Screenshot of the test pane with the runbok test complete displaying the output Hello World."></p>

4. You just want to start the runbook so click **Start** and then **Yes** when prompted.

5. A job pane is opened for the runbook job that you created. You can close this pane, but in this case you leave it open so you can watch the job's progress.

6. The job status is shown in Job Summary and matches the statuses that you saw when you tested the runbook.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow5.png" alt="Screenshot of the output pane with the runbok status of complete displaying."></p>
