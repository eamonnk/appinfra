
Manual execution of environment provisioning and configuration management is both laborious and error prone. DevOps advocates automation to reduce the probability of errors introduced through manual execution, and automation delivers the added advantage of being able to carry out the work more quickly without relying on subject experts. 

Microsoft Azure is built to support automation from the ground up. <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-intro/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Automation</span></a> is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment. The service saves time and increases the reliability of regular administrative tasks, and even schedules them to be automatically performed at regular intervals. You can automate processes using runbooks or automate configuration management by using Desired State Configuration (DSC).



<p style="text-align:center;"><img src="../Linked_Image_Files/azureautomation.png" alt="Icon representing Azure Automation"></p>

Azure Automation is not the only way to automate within Azure. You can use open-source tools to perform some of these operations, but the integration hooks available to Azure Automation remove much of the integration complexity that you would have to manage if you performed these operations manually.

The following are some of Azure Automation capabilities:

- *Process automation*: Azure Automation provides you the ability to automate frequent, time-consuming, and error-prone cloud management tasks. 
- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Automation State Configuration </span></a> - Azure Automation State Configuration is an Azure service that allows you to write, manage, and compile PowerShell Desired State Configuration (DSC) configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud. 
- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-update-management" target="_blank"><span style="color: #0066cc;" color="#0066cc">Update Management</span></a> -  Get visibility of update compliance across Azure, on-premises, and other clouds. You can create schedule deployments to orchestrate the installation of updates within a defined maintenance window. 
- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-solution-vm-management" target="_blank"><span style="color: #0066cc;" color="#0066cc">Start/Stop VMs</span></a> - Azure Automation provides an integrated **Start/Stop VMs** related resource to allow you to start and stop VMs on user-defined schedules, provides insights through Azure Log Analytics, and sends optional emails by using action groups. 
- <a href="https://docs.microsoft.com/en-us/azure/automation/source-control-integration" target="_blank"><span style="color: #0066cc;" color="#0066cc">Source control integration</span></a> - Can integrate with Github, Azure DevOps Git or TFVC repositories.
- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-config-aws-account" target="_blank"><span style="color: #0066cc;" color="#0066cc">Automate resources in Amazon Web Services (AWS)</span></a> - It is also possible to automate common tasks with resources in Amazon Web Services (AWS) using Automation runbooks in Azure.
- *Manage Shared resources*: Azure Automation consists of a set of shared resources, sch as connections, credentials, modules, schedules, variables and more, that make it easier to automate and configure your environments at scale.
- *Running backups* -  Azure Automation is very helpful for running regular backups of non-database systems, such as backing up Blob storage at certain intervals.

Azure Automation works across hybrid cloud environments and also for Windows as well as Linux.
