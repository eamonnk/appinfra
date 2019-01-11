<h1><strong><span style="color: #0000CD;">PowerShell Workflows</span></strong></h1>  

IT Pros often automate the management of their multi-device environments by running sequences of long-running tasks, or workflows, that can affect multiple managed computers or devices at the same time. Windows PowerShell Workflow lets IT Pros and developers leverage the benefits of <a href="https://docs.microsoft.com/en-us/previous-versions/dotnet/articles/ee342461(v=msdn.10)" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows Workflow Foundationk</span></a> with the automation capabilities and ease of Windows PowerShell. 

Windows PowerShell Workflow functionality was introduced in Windows Server® 2012 and Windows 8, and is part of Windows PowerShell 3.0 and newer releases of Windows PowerShell. Windows PowerShell Workflow helps automate the distribution, orchestration, and completion of multi-device tasks, freeing users and administrators to focus on higher-level tasks.

### Activities
An activity is a specific task that you want a workflow to perform. Just as a script is composed of one or more commands, a workflow is composed of one or more activities that are carried out in a sequence. A script can also be used as a single command in another script, and a workflow can be used as an activity within another workflow.

<a href="https://docs.microsoft.com/en-us/previous-versions/dotnet/articles/ee342461(v=msdn.10)" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows Workflow Foundationk</span></a>

### Workflow Characteristics
Workflow has the following characteristics:
- Can be long-running
- Can be repeated over and over 
- Can run tasks in parallel 
- Can be interrupted i.e. can be stopped and restarted, suspended and resumed
- Can also continue after an unexpected interruption, such as a network outage or computer restart

### Workflow Benefits

- *Windows PowerShell scripting syntax* - Is built on PowerShell.
- *Multidevice management* - Can simultaneously apply workflow tasks to hundreds of managed nodes. 
- *Running a single task to manage complex, end-to-end processes* - Can combine related scripts or commands that act on an entire scenario into a single workflow. Status and progress of activities within the workflow are visible at any time.
- *Automated failure recovery* -  Workflows survive both planned and unplanned interruptions, such as computer restarts. You can suspend workflow operation, then restart or resume the workflow from the point at which it was suspended. You can author checkpoints as part of your workflow, so that you can resume the workflow from the last persisted task (or checkpoint), instead of restarting the workflow from the beginning.
- *Connection and activity retries* - Can retry connections to managed nodes if network-connection failures occur. Workflow authors can also specify activities that must run again if the activity cannot be completed on one or more managed nodes (for example, if a target computer was offline while the activity was running).
- *Connect and disconnect* -  Users can connect and disconnect from the computer that is running the workflow, but the workflow remains running. For example, if you are running the workflow and managing the workflow on two different computers, you can log off of or restart the computer from which you are managing the workflow, and monitor workflow operations from another computer (such as a home computer) without interrupting the workflow.
- *Task scheduling* - Can be scheduled and then started when specific conditions are met, as with any other Windows PowerShell cmdlet or script.
