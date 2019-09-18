
The Hybrid Runbook Worker feature of Azure Automation allows you to run runbooks that manage local resources in your private datacenter, on machines located in your datacenter. Azure Automation stores and manages the runbooks, and then delivers them to one or more on-premises machines.

The Hybrid Runbook Worker functionality is presented in the following graphic:

<p style="text-align:center;"><img src="../Linked_Image_Files/dsc9.png" alt="Diagram of an Azure Automation Hybrid Runbook Worker workflow. The diagram is broken into two boxes. On the right, an Azure cloud box contains two separate boxes. The first box is labeled 'Azure Automation', and contains 'Runbooks' and 'DSC Configurations' icons. The second box is labeled 'Azure Resources'. On the left hand side is a box labelled 'on-premises', which contains icons representing 'Local Server' and 'Local Resources'. Another box is labelled 'Hybrid Runbook Work group', which contains icons representing 'Windows Hybrid Runbook Worker' and 'Linux Hybrid Runbook'."></p>

### Hybrid Runbook Worker workflow and characteristics

The following list are characteristics of the Hybrid Runbook Worker workflow:

- You can designate one or more computers in your datacenter to act as a Hybrid Runbook Worker, and then run runbooks from Azure Automation.
- Each Hybrid Runbook Worker is a member of a Hybrid Runbook Worker group, which you specify when you install the agent.
- A group can include a single agent, but you can install multiple agents in a group for high availability.
- There are no inbound firewall requirements to support Hybrid Runbook Workers, only Transmission Control Protocol (TCP) 443 is required for outbound internet access. 
- The agent on the local computer initiates all communication with Azure Automation in the cloud. 
- When a runbook is started, Azure Automation creates an instruction that is retrieved by the agent. The agent then pulls down the runbook and any parameters prior to running it. 


To manage configuring your on-premises servers that support the Hybrid Runbook Worker role with DSC, you must add them as DSC nodes. For further information about onboarding them for management with DSC, see <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding" target="_blank"><span style="color: #0066cc;" color="#0066cc">Onboarding machines for management by Azure Automation State Configuration</span></a>.

> **Note**: For more information on installing and removing Hybrid Runbook Workers and groups, see:
>
> - <a href="https://docs.microsoft.com/en-us/azure/automation/automation-hybrid-runbook-worker#installing-hybrid-runbook-worker" target="_blank"><span style="color: #0066cc;" color="#0066cc">Automate resources in your datacenter or cloud by using Hybrid Runbook Worker</span></a>
> - <a href="https://azure.microsoft.com/en-us/blog/hybrid-management-in-azure-automation/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Hybrid Management in Azure Automation</span></a>

