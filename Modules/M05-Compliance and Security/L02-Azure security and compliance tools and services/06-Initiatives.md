

Initiatives work alongside policies in Azure Policy. An *initiative definition* is a set of policy definitions to help track your compliance state for a larger goal. Even if you have a single policy, we recommend using initiatives if you anticipate increasing the number of policies over time.

Like a policy assignment, an *initiative assignment* is an initiative definition assigned to a specific scope. Initiative assignments reduce the need to make several initiative definitions for each scope. This scope could also range from a management group to a resource group. You assign initiatives in the same way you assign policies.


### Initiative definitions

Initiative definitions simplify the process of managing and assigning policy definitions by grouping a set of policies as one single item. For example, you could create an initiative named Enable Monitoring in Azure Security Center, with a goal to monitor all the available security recommendations in your Azure Security Center.

Under this initiative, you would have the following policy definitions:

- **Monitor unencrypted SQL Database in Security Center**. This policy definition is for monitoring unencrypted SQL databases and servers.
- **Monitor OS vulnerabilities in Security Center**. This policy definition is for monitoring servers that do not satisfy the configured baseline.
- **Monitor missing Endpoint Protection in Security Center**. This policy definition is for monitoring servers without an installed endpoint protection agent.


### Initiative assignments
Like a policy assignment, an *initiative assignment* is an initiative definition assigned to a specific scope. Initiative assignments reduce the need to make several initiative definitions for each scope. This scope could also range from a management group to a resource group.


> **Note**: You can read more about policy definition and structure at <a href="https://docs.microsoft.com/en-us/azure/governance/policy/concepts/definition-structure" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy definition structure</span></a>.
