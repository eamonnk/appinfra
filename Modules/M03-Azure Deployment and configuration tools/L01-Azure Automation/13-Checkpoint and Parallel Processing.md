<h1><strong><span style="color: #0000CD;">Checkpoints and Parallel Processing</span></strong></h1>

Workflows let you implement complex logic within your code. Two unique features of workflows are **checkpoints** and **parallel** **processing**.


<h2><span style="color: #0000CD;">Checkpoints</span></h2>

A [checkpoint](https://azure.microsoft.com/en-us/documentation/articles/automation-powershell-workflow/#checkpoints) is a snapshot of the current state of the workflow that includes the current value for variables and any output generated to that point. If a workflow ends in error or is suspended, the next time it is run it will start from its last checkpoint instead of the start of the workflow. You can set a checkpoint in a workflow with the **Checkpoint-Workflow** activity. For example, in the following sample code, if an exception occurs after Activity2, the workflow will end. When the workflow is run again, it starts with Activity2 because this followed just after the last checkpoint set.

```PowerShell
<Activity1>

Checkpoint-Workflow

<Activity2>

<Exception>

<Activity3>

```

<h2><span style="color: #0000CD;">Parallel processing</span></h2>

A [Parallel](https://azure.microsoft.com/en-us/documentation/articles/automation-powershell-workflow/#parallel-processing) script block has multiple commands that will run concurrently instead of sequentially, as occurs with a typical script. In the following example, two VMs will be started concurrently.

```PowerShell
Parallel

{

Start-AzureRmVM -Name $vm0 -ResourceGroupName $rg  
 Start-AzureRmVM -Name $vm1 -ResourceGroupName $rg

}
```
