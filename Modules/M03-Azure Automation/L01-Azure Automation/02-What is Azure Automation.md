The manual execution of environment provisioning and configuration management is both laborious and error prone. DevOps advocates for using automation to reduce the probability of introducing error through manual execution.  Automation has the added advantage of being able to carry out the work more quickly, and without relying on subject experts.

<p style="text-align:center;"><img src="../Linked_Image_Files/azureautomation.png" alt="Icon representing Azure Automation. The icon depicts a bolt of lightening between two mechanical, cog wheels."></p>

Microsoft Azure is built to support automation from the ground up. [Azure Automation](https://azure.microsoft.com/en-us/documentation/articles/automation-intro/) is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in cloud and enterprise environments. The Azure Automation service saves time and increases the reliability of regular administrative tasks, and even schedules them to be automatically performed at regular intervals. You can automate processes using runbooks or automate configuration management by using *Desired State Configuration* (DSC).

> :information_source: DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code. For information about Desired State Configuration (DSC) see the page [Windows PowerShell Desired State Configuration Overview](https://docs.microsoft.com/en-us/powershell/dsc/overview/overview).

Azure Automation is not the only way to automate within Azure. You can also use open-source tools to perform some of these operations. However, the integration hooks available to Azure Automation remove much of the integration complexity associated with managing and performing these operations manually.

### Azure Automation key capabilities

The following are some key capabilities of Azure Automation:

- *Process automation*. Azure Automation provides you with the ability to automate frequent, time-consuming, and error-prone cloud management tasks.
- *Configuration management*. [Azure Automation Desired State Configuration (DSC)](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) is an Azure service that allows you to write, manage, and compile PowerShell Desired State Configuration (DSC) configurations, import DSC Resources, and assign configurations to target nodes, all in the cloud.
- [*Update Management*](https://docs.microsoft.com/en-us/azure/automation/automation-update-management). Provides visibility of update compliance across Azure, on-premises, and other clouds. You can create schedule deployments to orchestrate the installation of updates within a defined maintenance window.
- [*Start/Stop VMs*](https://docs.microsoft.com/en-us/azure/automation/automation-solution-vm-management). Azure Automation provides an integrated Start/Stop VMs related resource to allow you to start and stop VMs, on user-defined schedules. It also provides insights through Azure Log Analytics, and can send emails using action groups (optional).
- [*Source control integration*](https://docs.microsoft.com/en-us/azure/automation/source-control-integration). Azure Automation can be integrated with Github, Azure DevOps Git or TFVC repositories.
- [*Automate resources in Amazon Web Services (AWS)*](https://docs.microsoft.com/en-us/azure/automation/automation-config-aws-account). It is also possible to automate common tasks with resources in Amazon Web Services (AWS) using Automation runbooks in Azure.
- *Manage Shared resources*. Azure Automation consists of a set of shared resources, such as connections, credentials, modules, schedules, variables and more, which make it easier to automate and configure your environments at scale.
- *Running backups*. Azure Automation is very helpful for running regular backups of non-database systems, such as backing up Blob storage at certain intervals.
- *Cross-platform support*. Azure Automation works across hybrid cloud environments, and also for Windows as well as Linux.
