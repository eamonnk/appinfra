
Azure Blueprints enable cloud architects to define a repeatable set of Azure resources that implement and adhere to an organization's standards, patterns, and requirements. Azure Blueprint enables development teams to rapidly build and deploy new environments with the knowledge that they're building within organizational compliance with a set of built-in components that speed up development and delivery.


<p style="text-align:left;"><img src="../Linked_Image_Files/azureblueprint.png" width="100" height="100" alt="Icon representing Azure Blueprint"></p>


Azure Blueprint is a declarative way to orchestrate the deployment of various resource templates and other artifacts, such as:

- Role assignments
- Policy assignments
- Azure Resource Manager templates
- Resource groups

The process of implementing Azure Blueprint consists of the following high-level steps:

1. Create an Azure Blueprint.
2. Assign the blueprint.
3. Track the blueprint assignments.

With Azure Blueprint, the relationship between the blueprint definition (what should be deployed) and the blueprint assignment (what was deployed) is preserved. This connection supports improved deployment tracking and auditing.

Azure Blueprints are different from Azure Resource Manager Templates.  When Azure Resource Manager Templates deploy resources, they have no active relationship with the deployed resources (they exist in a local environment or in source control). By contrast, with Azure Blueprint, each deployment is tied to an Azure Blueprint package.  This means that the relationship with resources will be maintained, even after deployment. Maintaining relationships, in this way, improves auditing and tracking capabilities.

### Usage Scenario
Adhering to security or compliance requirements, whether government or industry requirements, can be difficult and time-consuming. To help you with auditing, traceability, and compliance with your deployments, use Azure Blueprint artifacts and tools. Time-consuming paperwork is no longer needed, and your path to certification is expedited. 

Azure Blueprint are also useful in Azure DevOps scenarios, where blueprints are associated with specific build artifacts and release pipelines, and can be tracked more rigorously.

> **NOTE**: At the time of writing, Azure Blueprint is in preview and has not been released generally.


> **Note**: You can read more about Azure Blueprints at <a href="https://azure.microsoft.com/en-us/services/blueprints/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Blueprints</span></a>.