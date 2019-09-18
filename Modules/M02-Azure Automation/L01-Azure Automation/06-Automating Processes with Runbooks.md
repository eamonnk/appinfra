

A *runbook* is a set of tasks that perform some automated process in Azure Automation. It might be a simple process such as starting a VM and creating a log entry. Orr you might have a complex runbook that combines other smaller runbooks to perform a complex process across multiple resources, clouds, or on-premises environments. 

Traditionally, runbooks were a list of instructions that needed to be followed to complete an activity. Any activity that became a recurring task would usually end up with a runbook to reduce dependencies on specific individuals.

An example use case for a runbook would be to replace an existing manual process for truncating a SQL Azure database when it’s approaching maximum size. That current manual process includes multiple steps, such as connecting to the server, connecting to the database, getting the current size of database, checking if threshold has been exceeded and then truncating it, and finally notifying the user. 

Instead of performing each of these steps manually, you could create a runbook that would perform these tasks as a single process. You would start the runbook, provide the required information (such as the SQL server name, database name, and recipient email), and then wait while the process completes by itself.

### What can runbooks automate?

Runbooks in Azure Automation can do anything that PowerShell can do because they are based on Windows PowerShell or Windows PowerShell Workflow and Python2. If an application or service has an API, then a runbook can work with it. EXamples of some tasks that Azure Automation runbooks are capable of are"

- Automating resources in your on-premises datacenter of cloud using  <a href="https://docs.microsoft.com/en-us/azure/automation/automation-hybrid-runbook-worker" target="_blank"><span style="color: #0066cc;" color="#0066cc">Hybrid Runbook Worker</span>.</a>

- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-solution-vm-management" target="_blank"><span style="color: #0066cc;" color="#0066cc">Start/Stop Azure virtual machines during off-hours solution in Azure Automation</span></a> and autostop VMs based on low CPU usage, to optimize VM costs.

- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-scenario-aws-deployment" target="_blank"><span style="color: #0066cc;" color="#0066cc">Automate provisioning of a virtual machine in Amazon Web Services (AWS)</span></a>


- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-manage-send-joblogs-log-analytics#set-up-integration-with-log-analytics" target="_blank"><span style="color: #0066cc;" color="#0066cc">Forward job status and job streams from Automation to Log Analytics</span></a>. Send your Automation logs to Log Analytics for analysis and have alerts such as email configured to notify you of any failures or other relevant outcomes.



> **Note**: Before you can run a runbook, you must first publish it so it's available to run.
