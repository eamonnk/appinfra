
You can use the Update Management solution in Azure Automation to manage operating system updates:

- For computers running the Windows and Linux operating systems. 
- For computers deployed in Azure.
- In on-premises environments.
- In other cloud providers. 
 
You can also use Update Management to quickly assess the status of available updates on all agent computers, and manage the installation process for required server updates.


### Update Management solution overview
Computers that are managed by Update Management use the following configurations to perform assessments and update deployments:

- Microsoft Monitoring Agent (MMA) for Windows or Operations Management Suite (OMS) Linux Agent
- PowerShell DSC for Linux
- Automation Hybrid Runbook Worker
- Microsoft Update or Windows Server Update Services (WSUS) for computers running Windows operating systems i.e. the Windows Update Agent is a windows based agent that works with WSUS, or yum/apt/zypper which are package management services available on Linux.

The following diagram is a conceptual view of the behavior and data flow of how the Update Management solution assesses and applies security updates to all connected computers running the Windows Server and Linux operating systems in a workspace.


<p style="text-align:center;"><img src="../Linked_Image_Files/updatemanagement.png" alt="Workflow diagram of the Update management process with Azure Automation. a user runs a review update assessment and deployment status, and define deployment schedule. Update management runs the process for updating using pre-steps including package managers and post steps, in addition to hybrid runbook worker and a windows agent or Microsoft Operations Management suite (OMS) linux agent, the Windows Update Agent is a windows based agent that works with WSUS, or yum/apt/zypper which are package management services available on Linux."></p>

You can also use Update Management to natively onboard machines in multiple subscriptions in the same tenant.
