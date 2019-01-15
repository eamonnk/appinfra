Use a script editor, such as the *Windows PowerShell Integrated Scripting Environment* (ISE), to [write your workflows](https://azure.microsoft.com/en-us/documentation/articles/automation-first-runbook-textual/).

> :information_source: Windows PowerShell ISE auto compiles your workflow code, and allows you to save the artifact. The syntactic differences between scripts and workflows are significant, and Windows PowerShell ISE can distinguish workflows from scripts. Windows PowerShell ISE can also enforce strict adherence to the correct syntax, and highlight syntax errors. As a result, using Windows PowerShell ISE to write your workflows will save you significant coding and testing time.

### Syntax

Begin with the `workflow` keyword. The `workflow` keyword inform Windows PowerShell that you are working with workflows. The `workflow` keyword is required in a script workflow. The name of the workflow follows the `workflow` keyword. The body of the workflow is enclosed in braces. A workflow is a Windows PowerShell command type. Select a name with a verb-noun format.

  ```PowerShell
    workflow Test-Workflow

    {
      ...
    }
  ```

To add parameters to a workflow, use the `Param` keyword. These are the same techniques that you use to add parameters to a function. Lastly, simply add your standard PowerShell commands.

  ```PowerShell
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

1. In the Azure Portal, open your Automation Account.
2. Chose **Runbooks** under **Process Automation** to open the list of runbooks.
3. Create a new runbook by selecting the **+ Add a runbook** button, and then choosing **Create a new runbook**.
4. Give the runbook the name `MyFirstRunbook-Workflow`.
5. In this case, you're are creating a PowerShell Workflow runbook so, select **Powershell Workflow** as the **Runbook type**.
6. Choose **Create** to create the runbook and open the textual editor.

#### Add Code to a runbook

You can type code directly into the runbook. You can also select cmdlets, runbooks, and assets from the **Library Control** and add to the runbook with any related parameters. For this walkthrough, type directly into the runbook.

1. Type Write-Output 'Hello World.' between the braces, as shown below.

  ```PowerShell
    Workflow MyFirstRunbook-Workflow
    {
      Write-Output "Hello World"
    }
  ```

2. Save the runbook by choosing **Save**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1.png" alt="Screenshot of workflow editor containing cmdlets, runbooks and assets on the lefthand side. The sample code for this hello world sample is shown on the right side."></p>

#### Test the runbook

Before you publish the runbook to make it available in production, you need to test it to make sure that it works properly. When you test a runbook, you run its *Draft* version and view its output interactively.

1. Select the **Test** pane

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1.png" alt="Screenshot of Test Pane in the workflow editor."></p>

2. Choose **Start** to start the test. This should be the only enabled option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow2.png" alt="Screenshot of the test pane with the start button highlighted."></p>

3. A runbook job is created and its status displayed. The job status will start as *Queued*, indicating that it is waiting for a runbook worker in the cloud to come available. It moves to *Starting* when a worker claims the job, and then *Running* when the runbook actually starts running.

4. When the runbook job completes, its output is displayed. In this case, you should see 'Hello World'. Close the **Test** pane when finished.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow3.png" alt="Screenshot of the test pane showing the runbook test complete message and the output 'Hello World.' displayed."></p>

#### Publish and run the runbook

The runbook that you created is still in *Draft* mode. You need to publish runbook before you can start it in production. When you publish a runbook, you overwrite the existing *Published* version with the *Draft* version. In this case, you do not have an existing *Published* version yet because you have just created the runbook.

1. In the runbook editor choose **Publish** to publish the runbook, and then **Yes** when prompted.
2. To the left, your runbook should now be visible, in the **Runbooks** pane, with an **Authoring Status** shown as **Published**.
3. Move back to the right to view the pane for **MyFirstRunbook-Workflow**. The options across the top allow you to start, view, edit, link to a schedule for starting at a time in the future, add a webhook, delete or export.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow4.png" alt="Screenshot showing an overview of the MyFirstRunbook-Workflow in the webhooks pane."></p>

4. To start the runbook select **Start**, and then **Yes** when prompted.

5. A **Job** pane is opened for the runbook you created. Leave it open so that you can watch the job's progress.

6. The job status is shown in **Job Summary**. The job status states match those used for testing the runbook.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow5.png" alt="Screenshot of the output pane showing the runbook complete status ."></p>

> :information_source: The following summarizes the key benefits to using Windows PowerShell ISE for writing workflows.
>
> - auto compiles your code and allows you to save the artifact
> - can enforce strict adherence to the correct workflow syntax
> - highlight syntax errors
> - support workflows and scripts, and can distinguish between them
> - saves coding and testing time
