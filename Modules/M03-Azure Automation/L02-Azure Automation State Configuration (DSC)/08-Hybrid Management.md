The *Hybrid Runbook Worker* feature of Azure Automation allows you to run runbooks on machines located in your datacenter, to manage local resources. The runbooks are stored and managed in Azure Automation and then delivered to one or more on-premises machines.

The following image illustrates the Hybrid Runbook Worker functionality.

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc9.png" alt="Diagram of an Azure Automation Hybrid Runbook Worker workflow. The diagram is broken into two boxes. On the right, an Azure cloud box contains two separate boxes. The first box is labeled 'Azure Automation', and contains 'Runbooks' and 'DSC Configurations' icons. The second box is labeled 'Azure Resources'. On the left hand side is a box labelled 'on-premises', which contains icons representing 'Local Server' and 'Local Resources'. Another box is labelled 'Hybrid Runbook Work group', which contains icons representing 'Windows Hybrid Runbook Worker' and 'Linux Hybrid Runbook'."></p>

### Hybrid Runbook Worker workflow and characteristics

- You can designate one or more computers in your datacenter to act as a Hybrid Runbook Worker, and then run runbooks from Azure Automation.
- Each Hybrid Runbook Worker is a member of a Hybrid Runbook Worker group, which you specify when you install the agent.
- A group can include a single agent, but you can install multiple agents in a group for high availability.
- There are no inbound firewall requirements to support Hybrid Runbook Workers. Only TCP 443 is required for outbound internet access.
- The agent on the local computer initiates all communication with Azure Automation in the cloud.
- When a runbook is started, Azure Automation creates an instruction that is retrieved by the agent. The agent then pulls down the runbook and any parameters before running it.

To manage the configuration of your on-premises servers that support the Hybrid Runbook Worker role with Desired State Configuration (DSC), you must add them as DSC nodes. For further information about onboarding them for management with DSC, see the page [Onboarding machines for management by Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding).

> :information_source: For more information about installing and removing Hybrid Runbook Workers and groups, see the pages [Automate resources in your datacenter or cloud by using Hybrid Runbook Worker](https://docs.microsoft.com/en-us/azure/automation/automation-hybrid-runbook-worker#installing-hybrid-runbook-worker) and [Hybrid Management in Azure Automation](https://azure.microsoft.com/en-us/blog/hybrid-management-in-azure-automation/).
