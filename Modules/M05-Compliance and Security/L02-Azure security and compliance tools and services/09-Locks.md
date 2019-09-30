
*Locks* help you to prevent the accidental deletion or modification of your Azure resources. You can manage locks from within the Azure portal. To view, add, or delete locks for a resource in Azure portal, go to the **Settings** section on the resource's settings blade.

You may need to lock a subscription, resource group, or resource to prevent users from accidentally deleting or modifying critical resources. You can set a lock level to **CanNotDelete** or **ReadOnly**.

- CanNotDelete means that authorized users can read and modify a resource, but they cannot delete the resource.
- ReadOnly means that authorized users can read a resource, but they cannot delete or modify it.

In Azure portal, locks are called **Delete** and **Read-only** respectively.

> **Note**: You can read more about Locks on the <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-lock-resources" target="_blank"><span style="color: #0066cc;" color="#0066cc">Lock resources to prevent unexpected changes</span></a> webpage.
