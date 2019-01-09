<h1><strong><span style="color: #0000CD;">What Is Azure Automation? </span></strong></h1>

Manual execution of environment provisioning and configuration management is both laborious and error prone. DevOps advocates automation to reduce the probability of errors introduced through manual execution, and automation delivers the added advantage of being able to carry out the work more quickly without relying on subject experts. 

Microsoft Azure is built to support automation from the ground up. [Azure Automation](https://azure.microsoft.com/en-us/documentation/articles/automation-intro/) is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment. The service saves time and increases the reliability of regular administrative tasks, and even schedules them to be automatically performed at regular intervals. You can automate processes using runbooks or automate configuration management by using Desired State Configuration (DSC).

Azure Automation is not the only way to automate within Azure. You can use open-source tools to perform some of these operations, but the integration hooks available to Azure Automation remove much of the integration complexity that you would have to manage if you performed these operations manually.

The following are some common automation tasks:

*   Disaster recovery. Deploy new instances of Azure resources quickly within an alternative Azure datacenter after a disaster occurs. Resources might include Azure virtual machines (VMs), virtual networks, or cloud services, in addition to database servers.
*   Provisioning. Perform initial and subsequent provisioning of a complete deployment, for example, a virtual network, where you assign VMs to it, create cloud services, and join the services to the same virtual network.
*   State management. Apply DSC to manage the state of your machines.
*   Running backups. Azure Automation is very helpful for running regular backups of non-database systems, such as backing up Blob storage at certain intervals.
*   Deploying patches. Azure Automation allows you to develop a runbook to manage the updates at scheduled times to manage patch remediation. Ensure machines continually align with configured security policy.

