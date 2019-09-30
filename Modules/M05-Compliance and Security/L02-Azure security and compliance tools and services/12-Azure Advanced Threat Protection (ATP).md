
*Azure Advanced Threat Protection* (Azure ATP) is a cloud-based security solution that identifies and detects advanced threats, compromised identities, and malicious insider actions directed at your organization. Azure ATP is capable of detecting known malicious attacks and techniques, and can help you investigate security issues, and network vulnerabilities.

### Azure ATP components

Azure ATP consists of the following components.

- Azure ATP portal. Azure ATP has its own portal. Through Azure ATP portal, you can monitor and respond to suspicious activity. The Azure ATP portal allows you to manage your Azure ATP instance, and view data received from Azure ATP sensors.

	You can also use the Azure ATP portal to monitor, manage, and investigate threats to your network environment. You can sign in to the Azure ATP portal at <a href="https://portal.atp.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.atp.azure.com</span></a>. Note that you must sign in with a user account that is assigned to an Azure Active Directory (AD) security group that has access to the Azure ATP portal.
- Azure ATP sensor. Azure ATP sensors are installed directly on your domain controllers. The sensors monitor domain controller traffic without requiring a dedicated server or port mirroring configurations.
- Azure ATP cloud service. The Azure ATP cloud service runs on the Azure infrastructure, and is currently deployed in the United States, Europe, and Asia. The Azure ATP cloud service is connected to the Microsoft Intelligent Security Graph.

<p style="text-align:center;"><img src="../Linked_Image_Files/atp-sa-timeline.png" alt="Screenshot of the Azure Advanced Threat Protection dashboard and event timeline, showing security events such as HoneyToken activity, remote execution attempt detected, and suspicious service created."></p>

### Purchasing Azure ATP

Azure ATP is available as part of Microsoft's *Enterprise Mobility + Security E5* offering, and as a standalone license. You can acquire a license directly from the <a href="https://www.microsoft.com/en-ie/cloud-platform/enterprise-mobility-security-pricing" target="_blank"><span style="color: #0066cc;" color="#0066cc">Enterprise Mobility + Security Pricing Options</span></a> page, or through the Cloud Solution Provider (CSP) licensing model. Azure ATP is not available for purchase via the Azure portal.</a>

> **Note**: For more information about Azure ATP, review the <a href="https://azure.microsoft.com/en-us/features/azure-advanced-threat-protection/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Advanced Threat Protection</span></a> page.
