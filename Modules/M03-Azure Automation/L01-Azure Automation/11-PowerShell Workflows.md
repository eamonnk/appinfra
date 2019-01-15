IT professionals often automate the management of multi-device environments by running sequences of long-running tasks, or Workflows. Workflows can affect multiple, managed computers or devices at the same time.

*Windows PowerShell Workflow* lets IT professionals and developers leverage the benefits of <a href="https://docs.microsoft.com/en-us/previous-versions/dotnet/articles/ee342461(v=msdn.10)" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows Workflow Foundation</span></a> with the automation capabilities of Windows PowerShell. Windows PowerShell Workflow helps automate the distribution, orchestration, and completion of multi-device tasks, freeing users and administrators to focus on higher-level tasks.

### Activities

An activity is a specific task that you want a Workflow to perform. Just as a script is composed of one or more commands, a Workflow is composed of one or more activities that are carried out in a sequence. A script can also be used as a single command in another script, and a Workflow can be used as an activity within another Workflow.

### Windows PowerShell Workflow Characteristics

Windows PowerShell Workflows are well suited to performing the following kinds of activities.

- The activities within a Workflow can be long-running.
- Workflows can perform activities that need to be repeated many times.
- With Workflows, you can run many activities in parallel across multiple resources.
- Activities within a Workflow can be stopped and restarted easily. For example, a Workflow activity can be suspended and resumed after an unexpected network interruption or computer restart.

> :information_source: For information about Windows PowerShell Workflows see the page [Windows PowerShell Workflow Concepts](https://docs.microsoft.com/en-us/system-center/sma/overview-powershell-workflows?view=sc-sma-1807).

### Windows PowerShell Workflow Benefits

- *Windows PowerShell scripting syntax*. With Windows PowerShell Workflow you can leverage the power of the PowerShell scripting syntax.
- *Multidevice management*. You can apply Workflow tasks to hundreds of managed nodes simultaneously. 
- *Running a single task to manage complex, end-to-end processes*. Related scripts or commands that act on an entire scenario can be combined into a single Workflow. The status and progress of activities within the Workflow are then visible to you at any time.
- *Automated failure recovery*. Workflows survive both planned and unplanned interruptions, such as computer restarts. You can suspend Workflow operations, then restart or resume the Workflow from the point at which it was suspended. You can author checkpoints as part of your Workflow, so that you can resume the Workflow from the last persistent task (or checkpoint). Using checkpoint alleviates the need to restart a Workflow from the beginning.
- *Connection and activity retries*. Workflows make it possible to retry connections to managed nodes if network connection failures occur. Workflow authors can also specify activities that must run again if the activity cannot be completed on one or more managed nodes. For example, if a target computer was offline while the activity was running.
- *Connect and disconnect*. Users can connect and disconnect from the computer that is running the Workflow, but the Workflow remains running. For example, if you are running the Workflow and managing the Workflow on two different computers, you can log off of or restart the computer that is managing the Workflow, and monitor Workflow operations from another computer without interrupting the Workflow.
- *Task scheduling*. Activities can be scheduled and then started when specific conditions are met, as with any other Windows PowerShell cmdlet or script.

> :information_source: Arranging activities into Windows PowerShell Workflows can leverage the power of the PowerShell scripting syntax. The automation capabilities of PowerShell enables Windows PowerShell Workflow to automate the distribution, orchestration, and completion of multi-device tasks.
