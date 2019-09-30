
*Azure Policy* is an Azure service that you can use to create, assign, and, manage policies. Policies enforce different rules and effects over your Azure resources, which ensures that your resources stay compliant with your standards and service-level agreements (SLAs).

<p style="text-align:left;"><img src="../Linked_Image_Files/azurepolicy2.png" width="100" height="100" alt="Azure Policy icon"></p>

Azure Policy uses policies and initiatives to provide policy enforcement capabilities. Azure Policy evaluates your resources by scanning for resources that do not comply with the policies you create. For example, you may have a policy that specifies a maximum size limit for virtual machines (VMs) in your environment.

After you implement your maximum VM size policy, whenever a VM is created or updated, Azure Policy will evaluate the VM resource to ensure that the VM complies with the size limit that you set in your policy. Azure Policy can also evaluate your existing resources and configurations, and remediate non-compliant resources automatically. Azure Policy can help to maintain the state of your resources.

Azure Policy has built-in policy and initiative definitions for you to use. The definitions are arranged in categories, such as Storage, Networking, Compute, Security Center, and Monitoring.

Azure Policy can also integrate with Azure DevOps by applying any continuous integration (CI) and delivery pipeline (CD) policies that apply to the pre-deployment and post-deployment of your applications.

### CI/CD pipeline integration

An example of an Azure policy that you can integrate with your DevOps CI/CD pipeline is the *Check Gate* task. Check gate provides security and compliance assessment with Azure policies on the resources with an Azure resource group or subscription that you can specify. Check gate is available as a release pipeline deployment task.  

For more information see:

- <a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/azure-policy-check-gate?view=vsts" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy Check Gate task</span></a>
- <a href="https://azure.microsoft.com/en-us/services/azure-policy/
" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy</span></a>
