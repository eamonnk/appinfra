
To write the workflow, use a script editor such as the Windows PowerShell Integrated Scripting Environment (ISE). This enforces workflow syntax and highlights syntax errors. For more information, review the tutorial [My first PowerShell Workflow runbook](https://azure.microsoft.com/en-us/documentation/articles/automation-first-runbook-textual/).

A benefit of using PowerShell ISE is that it automatically compiles your code and allows you to save the artifact. Because the syntactic differences between scripts and workflows are significant, a tool that knows both workflows and scripts will save you significant coding and testing time.

### Syntax
When you create your workflow, begin with the **workflow** keyword, which identifies a workflow command to PowerShell. A script workflow requires the **workflow** keyword. Next, name the workflow, and have it follow the **workflow** keyword. The body of the workflow will be enclosed in braces.
 
A workflow is a Windows command type, so select a name with a verb-noun format:

```PowerShell
        workflow Test-Workflow
        
        {
           ...
        }
```

To add parameters to a workflow, use the **Param** keyword. These are the same techniques that you use to add parameters to a function. 

Finally, add your standard PowerShell commands.

```powershell
    workflow MyFirstRunbook-Workflow
    
    {
    Param(
        [string]$VMName,
        [string]$ResourceGroupName
        )
        ....
        Start-AzureRmVM -Name $VMName -ResourceGroupName $ResourceGroupName
    }
```
