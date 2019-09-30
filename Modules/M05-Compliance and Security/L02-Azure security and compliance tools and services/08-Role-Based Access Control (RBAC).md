
Role Based Access Control (RBAC) provides fine-grained access management for Azure resources, which enables you to grant users only the rights they need to perform their jobs. RBAC is provided at no additional cost to all Azure subscribers.

### Usage scenarios

The following examples provide use-case scenarios for RBAC:

- Allow a specific user to manage VMs in a subscription, and another user to manage virtual networks.
- Permit the database administrator (DBA) group management access to SQL Server databases in a subscription.
- Grant a user management access to certain types of resources in a resource group, such as VMs, websites, and subnets.
- Give an application access to all resources in a resource group.

To view access permissions, in a deployed virtual machine, open the **Access Control (IAM)** blade in the Azure portal. On this blade, you can view who has access, their role, and grant or remove access permissions.

<p style="text-align:center;"><img src="../Linked_Image_Files/accesscontrol1-2.png" alt="Screenshot of the Access control 9IAM) pane in Azure portal showing options to add, view and deny role assignments"></p>

The following illustration is an example of the **Access Control (IAM)** blade for a resource group. Note how the **Roles** tab shows the built-in roles that are available.

<p style="text-align:center;"><img src="../Linked_Image_Files/accesscontrol2-2.png" alt="Screenshot of the Roles blade in the Access control of Azure portal with built-in roles highlighted."></p>

A full list of available built-in roles can be found on the <a href="https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles" target="_blank"><span style="color: #0066cc;" color="#0066cc">Built-in roles for Azure resources</span></a> webpage.

RBAC uses an *allow model*.  This means that when you are assigned a role, RBAC *allows* you to perform certain actions, such as read, write, or delete. Therefore, if one role assignment grants you read permissions to a resource group, and a different role assignment grants you write permissions to the same resource group, you will have both read and write permissions for that resource group.

### Best practice

When using RBAC, segregate duties within your team and only grant users the access they need to perform their jobs. Instead of giving everybody unrestricted access to your Azure subscription and resources, allow only certain actions at a particular scope, i.e. grant users the minimal privileges that they need to complete their work.

> **Note**: For more information about RBAC, visit <a href="https://docs.microsoft.com/en-us/azure/role-based-access-control/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc"> What is role-based access control (RBAC)</span></a>?
