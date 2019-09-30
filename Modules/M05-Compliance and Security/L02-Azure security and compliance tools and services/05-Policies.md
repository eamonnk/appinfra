
Applying a policy to your resources with Azure Policy involves the following steps.

1. Policy definition. Create a policy definition.
2. Policy assignment. Assign the definition to a scope of resources.
3. Remediation. View the policy evaluation results, and address any non-compliances.

### Policy definition

A *policy definition* specifies the resources to be evaluated, and the actions to take on them. For example, you could prevent VMs from deploying if they are exposed to a public IP address. You could also prevent a particular hard disk from being used when deploying VMs, to control costs. Policies are defined in the Java Script Object Notation (JSON) format.

The following example defines a policy that limits where you can deploy resources.

```json
{
    "properties": {
        "mode": "all",
        "parameters": {
            "allowedLocations": {
                "type": "array",
                "metadata": {
                    "description": "The list of locations that can be specified when deploying resources",
                    "strongType": "location",
                    "displayName": "Allowed locations"
                }
            }
        },
        "displayName": "Allowed locations",
        "description": "This policy enables you to restrict the locations your organization can specify when deploying resources.",
        "policyRule": {
            "if": {
                "not": {
                    "field": "location",
                    "in": "[parameters('allowedLocations')]"
                }
            },
            "then": {
                "effect": "deny"
            }
        }
    }
}
```

The following is a list of example policy definitions.

- Allowed Storage Account SKUs. This policy defines conditions (or *rules*) that limit storage accounts to a set of specified sizes, or Stock Keeping Units (SKUs). Its effect is to deny all storage accounts that do not adhere to the set of defined SKU sizes.
- Allowed Resource Type. This policy definition has a set of conditions to specify the resource types that can be deployed. Its effect is to deny all resources that are on the list.
- Allowed Locations. This policy restricts the locations that new resources can be deployed to. It is used to enforce geographic compliance requirements.
- Allowed Virtual Machine SKUs. This policy specifies a set of virtual machine SKUs that can be deployed. The policy effect is that VMs cannot be deployed from unspecified SKUs.

### Policy assignment

Policy definitions, whether custom or built in, need to be assigned. A *policy assignment* is a policy definition that has been assigned to a specific scope. Scope can range from a management group to a resource group. Child resources will inherit any policy assignments that have been applied to their parents. This means that if a policy is applied to a resource group, it is also applied to all the resources within that resource group. However, you can define subscopes for excluding particular resources from policy assignments.

You can assign policies via:

- Azure Portal
- Azure CLI
- PowerShell

### Remediation

Resources found not to comply to a `deployIfNotExists` or `modify` policy condition can be put into a compliant state through *Remediation*. Remediation instructs Azure Policy to run the `deployIfNotExists` effect, or the tag operations, of the policy on existing resources. You can bring resources into compliance using automated *bulk remediation*, instead of going through them one at a time, to minimize configuration drift.

> **Note**: You can read more about Azure Policy on the <a href="https://azure.microsoft.com/en-us/services/azure-policy/
" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy</span></a> webpage.
