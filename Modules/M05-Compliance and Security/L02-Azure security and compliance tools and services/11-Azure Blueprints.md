
Azure Blueprints enables cloud architects to define a repeatable set of Azure resources that implement and adhere to an organization's standards, patterns, and requirements. Azure Blueprints helps development teams to build and deploy new environments rapidly, within organizational compliance requirements, with a set of built-in components that speed up development and delivery.

<p style="text-align:left;"><img src="../Linked_Image_Files/azureblueprint.png" width="100" height="100" alt="Icon representing Azure Blueprints"></p>

Azure Blueprints provides a declarative way to orchestrate deployment for various resource templates and artifacts, including:

- Role assignments
- Policy assignments
- Azure Resource Manager templates
- Resource groups

To implement Azure Blueprints complete the following steps.

1. Create a blueprint.
2. Assign the blueprint.
3. Track the blueprint assignments.

With Azure Blueprints, the relationship between the blueprint definition (what *should be* deployed) and the blueprint assignment (what *is* deployed) is preserved.

The blueprints in Azure Blueprints are different from Azure Resource Manager templates.  When Azure Resource Manager templates deploy resources, they have no active relationship with the deployed resources (they exist in a local environment or in source control). By contrast, with Azure Blueprints, each deployment is tied to an Azure Blueprints package. This means that the relationship with resources will be maintained, even after deployment. Maintaining relationships, in this way, improves deployment tracking and auditing capabilities.

### Usage scenario

Adhering to security and compliance requirements, whether government, industry, or organizational requirements, can be difficult and time consuming. To help you to trace your deployments, and to audit them for compliance, Azure Blueprints uses artifacts and tools that expedite your path to certification.

Azure Blueprints is also useful in Azure DevOps scenarios where blueprints are associated with specific build artifacts and release pipelines, and blueprints can be tracked rigorously.

> **Note**: At the time of writing, Azure Blueprints is in preview and is not available on general release.

You can learn more about Azure Blueprints at <a href="https://azure.microsoft.com/services/blueprints/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Blueprints</span></a>.
