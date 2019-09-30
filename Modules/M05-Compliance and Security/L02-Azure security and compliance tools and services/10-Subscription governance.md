
The following considerations apply to creating and managing Azure subscriptions.

- Billing. Billing reports can be generated for Azure subscriptions. If, for example, you have multiple internal departments and need to perform a chargeback, you can create a subscription for a department or project.

- Access Control. A subscription acts as a deployment boundary for Azure resources. Every subscription is associated with an Azure Active Directory (Azure AD) tenant that provides administrators with the ability to set up RBAC. When designing a subscription model, consider the deployment boundary. Some customers keep separate subscriptions for development and production, managed using RBAC, to isolate one subscription from the other (from a resource perspective).

- Subscription Limits. Subscriptions are bound by hard limitations. For example, the maximum number of Azure ExpressRoute circuits per subscription is 10. If you reach a limit, there is no flexibility. You should consider these limits during your design phase. If you need to exceed the limits, you may require additional subscriptions.

### Management groups

*Management Groups* can assist you with managing your Azure subscriptions. Management groups manage access, policies, and compliance across multiple Azure subscriptions. They allow you to order your Azure resources hierarchically into collections. Management groups facilitate the management of resources at a level above the level of subscriptions.

In the following image, access is divided across different regions and business functions, such as marketing and IT. This can be further divided into separate subscriptions for Dev and QA, or for specific teams, to track costs and resource usage at a granular level, add security layers, and segment workloads. Tightly restricting access to production subscriptions can enhance security.

<p style="text-align:center;"><img src="../Linked_Image_Files/subscriptions1-2.png" alt="Graphic representing Azure subscription management groups and how they can be structured for use as deployment boundaries."></p>

You can manage your Azure subscriptions more effectively by using Azure Policy and Azure RBACs. These tools provide distinct governance conditions that you can apply to each management group. Any conditions that you apply to a management group will be inherited by the resources and subscriptions within that group automatically.

> **Note**: For more information about management groups and Azure, read the <a href="https://docs.microsoft.com/en-us/azure/governance/management-groups/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Organize your resources with Azure management groups</span></a> webpage.
