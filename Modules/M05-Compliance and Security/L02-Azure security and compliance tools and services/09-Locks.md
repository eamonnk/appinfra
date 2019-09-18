
*Locks* help you prevent accidental deletion or modification of your Azure resources. You can manage these locks from within the Azure portal. To view, add, or delete locks, go to the **SETTINGS** section of any resource's settings blade.

You may need to lock a subscription, resource group, or resource to prevent other users in your organization from accidentally deleting or modifying critical resources. You can set the lock level to **CanNotDelete** or **ReadOnly**:

- **CanNotDelete** means authorized users can still read and modify a resource, but they can't delete the resource. 
- **ReadOnly** means authorized users can read a resource, but they can't delete or update it. Applying this lock is similar to restricting all authorized users to the permissions granted by the Reader role.

In the Azure portal, the locks are called ****Delete*** and **Read-only** respectively.

> **Note**: You can read more about Locks at <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-lock-resources" target="_blank"><span style="color: #0066cc;" color="#0066cc">Lock resources to prevent unexpected changes</span></a>.
