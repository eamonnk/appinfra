<h1><strong><span style="color: #0000CD;">Workflow Syntax</span></strong></h1>  

To [write the workflow](https://azure.microsoft.com/en-us/documentation/articles/automation-first-runbook-textual/), use a script editor, such as the Windows PowerShell Integrated Scripting Environment (ISE), which enforces workflow syntax and highlights syntax errors. A benefit of using this tool is that it auto compiles your code and allows you to save the artifact. The syntactic differences between scripts and workflows are significant, so a tool that knows workflows, as well as scripts, will save you significant coding and testing time.

Begin with the **workflow** keyword, which identifies a workflow command to Windows PowerShell. The **workflow** keyword is required in a script workflow. The name of the workflow follows the **workflow** keyword. The body of the workflow is enclosed in braces. A workflow is a Windows PowerShell command type. Select a name with a verb-noun format.

```PowerShell
**workflow Test-Workflow**

**{**

**...**

**}**

To add parameters to a workflow, use the **Param** keyword. These are the same techniques that you use to add parameters to a function. Lastly, simply add your standard PowerShell commands.

**workflow MyFirstRunbook-Workflow**

**{**

**Param(**

**[string]$VMName,**

**[string]$ResourceGroupName**

**)**

**....**

**Start-AzureRmVM -Name $VMName -ResourceGroupName $ResourceGroupName**

**}**
```
