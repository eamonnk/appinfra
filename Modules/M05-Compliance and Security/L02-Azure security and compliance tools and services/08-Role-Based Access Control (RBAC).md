

RBAC provides fine-grained access management for Azure resources, which enables you to grant users only the rights they need to perform their jobs. RBAC is provided at no additional cost to all Azure subscribers.

### Usage scenarios

Examples of when you might use RBAC include when you want to:

- Allow one user to manage VMs in a subscription, and another user to manage virtual networks.
- Allow a database administrator (DBA) group to manage SQL Server databases in a subscription.
- Allow a user to manage all resources in a resource group, such as VMs, websites, and subnets.
- Allow an application to access all resources in a resource group.

To view access permissions, in a deployed virtual machine, open the **Access Control (IAM)** blade in the Azure portal. On this blade, you can view who has access to an area and their role as well as grant or remove access.

<p style="text-align:center;"><img src="../Linked_Image_Files/accesscontrol1.png" width="500" height="250" alt="Screenshot of the Access control 9IAM) pane, shpwing the options to add a role assignment, view role assignment and View deny assignments"></p>


The following illustration is an example of the **Access Control (IAM)** blade for a resource group and on the Roles tab which is displaying some of the available builtin roles.


<p style="text-align:center;"><img src="../Linked_Image_Files/accesscontrol2.png" width="500" height="250" alt="Screenshot of the Access control (IAM)- Roles blade, with a sa ple of available builtinRoles listed and highlighted."></p>


A full list of available built-in roles can be found at available on the <a href="https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles" target="_blank"><span style="color: #0066cc;" color="#0066cc">Built-in roles for Azure resources</span></a> page.


RBAC uses an *allow model*.  This means that when you are assigned a role, RBAC *allows* you to perform certain actions, such as read, write, or delete. Therefore, if one role assignment grants you read permissions to a resource group, and a different role assignment grants you write permissions to the same resource group, you will have both read and write permissions on that resource group.


### Best practice

When using RBAC, segregate duties within your team and grant only the amount of access to users that they need to perform their jobs. Instead of giving everybody unrestricted permissions in your Azure subscription or resources, allow only certain actions at a particular scope i.e. grant users the lowest privilege level that they need to do their work.





> **Note**: For more information about RBAC, visit <a href="https://docs.microsoft.com/en-us/azure/role-based-access-control/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc"> What is role-based access control (RBAC)?</span></a>.
