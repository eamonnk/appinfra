
You can integrate Azure Security Center into your workflows and use it in many ways. The following provides two example usage scenarios.

1. Use Azure security center as part of your incident response plan.

    Many organizations only respond to security incidents after an attack has occurred. To reduce costs and damage, it is important to have an incident response plan in place *before* an attack occurs.

    <p style="text-align:center;"><img src="../Linked_Image_Files/security-center-incident-response-fig1.png" alt="A set of circles linked with arrows illustrate the relationships between the detection, assessment, diagnosis, stabilization and closure stages of an incident response plan."></p>

    The following are examples of how Azure security center can be used at the detect, assess, and diagnose stages of your incident response plan.

    - Detect. Review the first indication of an event investigation. For example, use the Azure security center dashboard to review the initial verification that a high-priority security alert has been raised.
    - Assess. Perform the initial assessment to obtain more information about a suspicious activity. For example, you can obtain more information from Azure security center about a security alert.
    - Diagnose. Conduct a technical investigation and identify containment, mitigation, and workaround strategies. For example, you can follow the remediation steps described by Azure security center for a particular security alert.

2. Use Azure security center recommendations to enhance security.

    You can reduce the chances of a significant security event by configuring a security policy, and then implementing the recommendations provided by Azure security center.

    A *security policy* defines the set of controls that are recommended for resources within a specified subscription or resource group. In Azure security center, you can define policies according to your company's security requirements.

    Azure security center analyzes the security state of your Azure resources. When security center identifies potential security vulnerabilities, it creates recommendations based on the controls set in the security policy. The recommendations guide you through the process of configuring the corresponding security controls.

    For example, if you have workloads that do not require the Azure SQL Database Transparent Data Encryption (TDE) policy, turn off the policy at the subscription level and enable it only on the resource groups where SQL Database TDE is required.

> **Note**: You can read more about Azure security center at <a href="https://azure.microsoft.com/en-us/services/security-center/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> Azure security center</span></a>. More implementation and scenario details are also available in the <a href="https://docs.microsoft.com/en-us/azure/security-center/security-center-planning-and-operations-guide" target="_blank"><span style="color: #0066cc;" color="#0066cc"> Azure security center planning and operations guide</span></a>.
