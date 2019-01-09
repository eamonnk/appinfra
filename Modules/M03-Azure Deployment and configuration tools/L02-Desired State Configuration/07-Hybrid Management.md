

The Hybrid Runbook Worker feature of Azure Automation allows you to run runbooks on machines located in your datacenter to manage local resources. The runbooks are stored and managed in Azure Automation and then delivered to one or more on-premises machines:

![Screenshot of an Azure Automation Hybrid Runbook Worker diagram. The diagram is broken into three boxes. On the right, an Azure cloud box contains three separate boxes and a Virtual Machines icon. The first box is labeled Azure Automation, and contains Runbooks and DSC Configurations icons. The second Box is labeled Azure Resources. The third box is labeled OMS Workspace, and contains an Automation Solution icon. On the top, left, is a Local box with Local Server, Local Resources, and Hybrid Runbook Worker icons. On the bottom, left is an Internet box with an External Resources icon. (At this time, we are unable to capture all of the directional flow information in the diagram. Future versions of this course should address this.]( ../../Linked_Image_Files/2.3.6.png)

You can designate one or more computers in your datacenter to act as a Hybrid Runbook Worker and then run runbooks from Azure Automation. Each worker requires the Microsoft management agent with a connection to Microsoft Operations Management Suite and the Azure Automation runbook environment. Operations Management Suite is only used to install and maintain the management agent and to monitor the functionality of the worker. Azure Automation performs the delivery of runbooks and the instruction to run them.

There are no inbound firewall requirements to support Hybrid Runbook Workers. Only TCP 443 is required for outbound internet access. The agent on the local computer initiates all communication with Azure Automation in the cloud. When a runbook is started, Azure Automation creates an instruction that is retrieved by the agent. The agent then pulls down the runbook and any parameters before running it. It will also retrieve any [assets](http://msdn.microsoft.com/library/dn939988.aspx) that are used by the runbook from Azure Automation.

To manage the configuration of your servers that support the Hybrid Runbook Worker role with Desired State Configuration (DSC), you must add them as DSC nodes. For further information about onboarding them for management with DSC, see [Onboarding machines for management by Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding).

Each Hybrid Runbook Worker is a member of a Hybrid Runbook Worker group that you specify when you install the agent. A group can include a single agent, but you can install multiple agents in a group for high availability.

When you start a runbook on a Hybrid Runbook Worker, you specify the group that it will run on. The members of the group will determine which worker will service the request. You cannot specify a specific worker.

For more information on installing and removing Hybrid Runbook Workers and groups, see [Installing Hybrid Runbook Worker](https://docs.microsoft.com/en-us/azure/automation/automation-hybrid-runbook-worker#installing-hybrid-runbook-worker) and [Hybrid Management in Azure Automation](https://azure.microsoft.com/en-us/blog/hybrid-management-in-azure-automation/).
