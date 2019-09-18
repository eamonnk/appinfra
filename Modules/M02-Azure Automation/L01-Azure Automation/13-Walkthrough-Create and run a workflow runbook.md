
This walkthrough will create a new PowerShell workflow runbook, test,  publish and then run the runbook.


### Prerequisites
-  Note: You require an Azure subscription to perform the following steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps


#### Create a new runbook
1. In the **Azure portal**, open your Automation account.
2. Under **Process Automation**, select **Runbooks** to open the list of runbooks.
3. Create a new runbook by selecting the **Create a new runbook**.
4. Give the runbook the name **MyFirstRunbook-Workflow**.
5. You're going to create a PowerShell Workflow runbook, so for **Runbook type**, select **Powershell Workflow**.
6. Select **Create** to create the runbook and open the text editor.

#### Add code to a runbook
You have two options when adding code to a runbook. You can type code directly into the runbook, or you can select cmdlets, runbooks, and assets from the Library control and have them added to the runbook, along with any related parameters. 

For this walkthrough, you'll use the type directly into the runbook method, as detailed in the following steps:

1. Type **Write-Output "Hello World."** between the braces, as per the below:

    ```Powershell
    Workflow MyFirstRunbook-Workflow
    {
    Write-Output "Hello World"
    }
    ```

2. Save the runbook by selecting **Save**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1.png" alt="Screenshot of workflow editor containing cmdlets, runbooks, and assets in the left pane, and the sample code on the right for the &quothello world&quot sample."></p>

#### Test the runbook
Before you publish the runbook to production, you want to test it to ensure that it works properly. When you test a runbook, you run the draft version and view its output interactively, as demonstrated in the following steps:

1. Select the **Test** pane.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow1a.png" alt="Screenshot of workflow editor highlighting Test Pane button."></p>

2. Select **Start** to start the test. This should be the only enabled option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow2.png" alt="Screenshot of the test pane with the start button called out."></p>

A runbook job is created and its status displayed. The job status will start as Queued indicating that it is waiting for a runbook worker in the cloud to come available. It moves to Starting when a worker claims the job, and then Running when the runbook actually starts running. When the runbook job completes, its output displays. In your case, you should see Hello World. 
    
4. When the runbook job finishes, close the **Test pane**. 

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow3.png" alt="Screenshot of the test pane with the runbook displaying Completed, and the output Hello World."></p>

#### Publish and run the runbook
The runbook that you created is still in draft mode. You need to publish it before you can run it in production. When you publish a runbook, you overwrite the existing published version with the draft version. In your case, you don't have a published version yet because you just created the runbook.

Use the following steps to publish your runbook:

1. In the runbook editor, select **Publish** to publish the runbook.
2. When prompted, select **Yes**.
2. Scroll left to view the runbook in the Runbooks pane, and ensure that it shows an **Authoring Status** of **Published**.
3. Scroll back to the right to view the pane for **MyFirstRunbook-Workflow**. Notice the options across the top:
	-	Start
	-	View
	-	Edit
	-	Link to schedule to start at some time in the future
	-	Add a webhook
	-	Delete
	-	Export
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow4.png" alt="Screenshot of the powershell workflow runbook overview pane."></p>

4. You just want to start the runbook, so select **Start**, and then when prompted, select **Yes**.

5. When the job pane opens for the runbook job that you created, leave it open so you can watch the job's progress.

6. Verify that at when the job completes, the job statuses that display in **Job Summary** match the statuses that you saw when you tested the runbook.

    <p style="text-align:center;"><img src="../Linked_Image_Files/workflow5.png" alt="Screenshot of the output pane with the runbook job status of completed."></p>
