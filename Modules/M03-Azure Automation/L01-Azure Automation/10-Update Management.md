
You can use the Update Management solution in Azure Automation to manage operating system updates for your Windows and Linux computers that are deployed in Azure, in on-premises environments, or in other cloud providers. You can quickly assess the status of available updates on all agent computers and manage the process of installing required updates for servers.


### Solution overview
Computers that are managed by Update Management use the following configurations to perform assessment and update deployments:
- Microsoft Monitoring Agent (MMA) for Windows or Linux
- PowerShell Desired State Configuration (DSC) for Linux
- Automation Hybrid Runbook Worker
- Microsoft Update or Windows Server Update Services (WSUS) for Windows computers

The following diagram shows a conceptual view of the behavior and data flow with how the solution assesses and applies security updates to all connected Windows Server and Linux computers in a workspace:


<p style="text-align:center;"><img src="../Linked_Image_Files/updatemanagement.png" alt="Workflow diagram of Update management process with Azure Automation starting with review update and define deployment schedule, with an arrow pointing to a process and two arrows also pointing to the same process from a box containing the process for updating using pre-steps, updates using package managers and post steps, as well as hybrid runbook worker and windows agent or OMS Linux agent."></p>

Update Management can be used to natively onboard machines in multiple subscriptions in the same tenant
