A runbook is a set of tasks that perform some automated process in Azure Automation. Processes within a runbook can be simple, such as starting a virtual machine and creating a log entry. Runbooks can also be combined to perform complex processes, across multiple resources, on multiple clouds and on-premises environments.

Traditionally, runbooks were lists of instructions that needed to be followed to complete an activity. Any activity that became a recurring task would usually end up with a runbook, to reduce dependencies on specific individuals.

> #### Common use case for a runbook
>
> Imagine that you have defined a process for manually truncating an Azure SQL database, whenever the database approaches its maximum size. You process involves the following steps:
> - connecting to the server
> - connecting to the database
> - getting the current size of database
> - comparing the database size to the maximum size threshold
> - truncating the database
> - sending a notification to the user
>
> Instead of manually performing these steps, you could create a runbook that would perform the tasks as a single process. You would start the runbook, provide the required information such as the SQL server name, database name, and recipient email, and then sit back while the process completes.

### What can Runbooks automate?

Runbooks in Azure Automation are based on Windows PowerShell or Windows PowerShell Workflow and Python2, so they can perform the same tasks as PowerShell. If an application or service has an API, then a runbook can work with it. The following are example tasks that can be performed by Azure Automation runbooks.

- Automate resources in your on-premises datacenter of cloud using [Hybrid Runbook Worker](https://docs.microsoft.com/en-us/azure/automation/automation-hybrid-runbook-worker)
- [Start/Stop Azure virtual machines](https://docs.microsoft.com/en-us/azure/automation/automation-solution-vm-management) during off-hours solution in Azure Automation, and automatically stop VMs based on low CPU usage, to optimize VM costs.
- [Automate the provisioning of a virtual machine in Amazon Web Services (AWS)](https://docs.microsoft.com/en-us/azure/automation/automation-scenario-aws-deployment)
- [Forward job status and job streams from Automation to Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-manage-send-joblogs-log-analytics#set-up-integration-with-log-analytics). Send your Automation logs to Log Analytics for analysis, and receive notifications of failures or other relevant outcomes, for example, by email alert.

> :information_source:: A runbook must be published before you can start it. Publishing the runbook makes it available for starting. For more information see the page [My first PowerShell runbook](https://docs.microsoft.com/en-us/azure/automation/automation-first-runbook-textual-powershell)
