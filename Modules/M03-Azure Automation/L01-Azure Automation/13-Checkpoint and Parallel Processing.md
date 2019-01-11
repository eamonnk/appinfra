

Workflows let you implement complex logic within your code. Two features available with workflows are:
 
- **checkpoints** 
- **parallel processing**.


### Checkpoints

A <a href="https://docs.microsoft.com/en-us/azure/automation/automation-powershell-workflow#checkpoints" target="_blank"><span style="color: #0066cc;" color="#0066cc">checkpoint</span></a> is a snapshot of the current state of the workflow that includes the current value for variables and any output generated to that point. 

If a workflow ends in error or is suspended, the next time it is run it will start from its last **checkpoint** instead of the start of the workflow. You can set a checkpoint in a workflow with the **Checkpoint-Workflow** activity. 

For example, in the following sample code, if an exception occurs after Activity2, the workflow will end. When the workflow is run again, it starts with Activity2 because this followed just after the last checkpoint set.

```PowerShell
    <Activity1>
        Checkpoint-Workflow
            <Activity2>
                <Exception>
            <Activity3>
```

### Parallel processing

A <a href="https://docs.microsoft.com/en-us/azure/automation/automation-powershell-workflow#parallel-processing" target="_blank"><span style="color: #0066cc;" color="#0066cc">Parallel processing</span></a> script block has multiple commands that will run concurrently, or in parallel, instead of sequentially, as occurs with a typical script. In the following example, two *vm0* and *vm1* will be started concurrently, and *vm2* will only start after *vm0* and *vm1* have started.

```PowerShell
    Parallel
    {
        Start-AzureRmVM -Name $vm0 -ResourceGroupName $rg  
        Start-AzureRmVM -Name $vm1 -ResourceGroupName $rg
    }

    Start-AzureRmVM -Name $vm2 -ResourceGroupName $rg  
```

Another example would be the below and it introduces some additional options.

- **ForEach -Parallel** - You can use the **ForEach -Parallel** construct to process commands for each item in a collection concurrently. The items in the collection are processed in parallel while the commands in the script block run sequentially. In the sample below, *Activity1* starts at the same time for all items in the collection. For each item, *Activity2* starts after *Activity1* is complete. *Activity3* starts only after both *Activity1* and *Activity2* have completed for all items.

- **ThrottleLimit** - We use the **ThrottleLimit** parameter to limit the parallelism. Too high of a **ThrottleLimit** can cause problems. The ideal value for the ThrottleLimit parameter depends on many factors in your environment. You should try start with a low value and try different increasing values until you find one that works for your specific circumstance.

```powershell
ForEach -Parallel -ThrottleLimit 10 ($<item> in $<collection>)
{
    <Activity1>
    <Activity2>
}
<Activity3>
```

A real world example of this could be as below, where a message is displayed for each file after it copies. Only after they are all completely copied is the final completion message displayed.

```powershell
    Workflow Copy-Files
    {
        $files = @("C:\LocalPath\File1.txt","C:\LocalPath\File2.txt","C:\LocalPath\File3.txt")
    
        ForEach -Parallel -ThrottleLimit 10 ($File in $Files)
        {
            Copy-Item -Path $File -Destination \\NetworkPath
            Write-Output "$File copied."
        }
    
        Write-Output "All files copied."
    }
```