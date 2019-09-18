
Azure Blueprints enables cloud architects to define a repeatable set of Azure resources that implement and adhere to an organization's standards, patterns, and requirements. Azure Blueprints helps development teams rapidly build and deploy new environments with the knowledge that they're building within organizational compliance, and with a set of built-in components that speed up development and delivery.


<p style="text-align:left;"><img src="../Linked_Image_Files/azureblueprint.png" width="100" height="100" alt="Azure Blueprints icon"></p>


Azure Blueprints is a declarative way to orchestrate deployment for various resource templates and other artifacts, such as:

- Role assignments
- Policy assignments
- Azure Resource Manager templates
- Resource groups

The process of implementing Azure Blueprints consists of the following high-level steps:

1. Create an Azure Blueprints blueprint.
2. Assign the blueprint.
3. Track the blueprint assignments.

With Azure Blueprints, the relationship between the blueprint definition (what *should be* deployed) and the blueprint assignment (what *is* deployed) is preserved. This connection supports improved deployment tracking and auditing.

The blueprints in Azure Blueprints are different from Azure Resource Manager templates.  When Azure Resource Manager templates deploy resources, they have no active relationship with the deployed resources (they exist in a local environment or in source control). By contrast, with Azure Blueprints, each deployment is tied to an Azure Blueprints package. This means that the relationship with resources will be maintained, even after deployment. In this way, maintaining relationships improves auditing and tracking capabilities.

### Usage scenario
Adhering to security or compliance requirements, whether government, industry, or organization requirements, can be difficult and time consuming. To help you with auditing, traceability, and compliance with your deployments, use Azure Blueprints artifacts and tools to expedite your path to compliance and certification. 

Azure Blueprints is also useful in Azure DevOps scenarios where blueprints are associated with specific build artifacts and release pipelines, and can be tracked more rigorously.

> **Note**: At the time of writing, Azure Blueprints is in preview and has not yet been released publicly.


You can learn more about Azure Blueprints at <a href="https://azure.microsoft.com/en-us/services/blueprints/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Blueprints</span></a>.
