


*Azure Policy* is a service in Azure that you use to create, assign, and, manage policies. These policies enforce different rules and effects over your resources, so those resources stay compliant with your corporate standards and service-level agreements (SLAs).


<p style="text-align:left;"><img src="../Linked_Image_Files/azurepolicy2.png" width="100" height="100" alt="Icon representing Azure Policy"></p>

Azure Policy does this by using policies and initiatives. It runs evaluations of your resources and scans for those not compliant with the policies you have created. For example, you can have a policy to allow only a certain stock keeping unit (SKU) size of virtual machines (VMs) in your environment. Once you implement this policy, it will evaluate resources when you create new ones or update existing ones. It will also evaluate your existing resources. 

Azure Policy comes with a number of built-in policy and initiative definitions that you can use, under categories such as Storage, Networking, Compute, Security Center, and Monitoring.

Azure Policy can also integrate with Azure DevOps, by applying any continuous integration and delivery pipeline policies that apply to the pre-deployment and post-deployment of your applications.

Azure Policy also has the ability to automatically remediate resources and configurations that are deemed non-compliant, thus ensuring the integrity of the state of the resources.

### CI/CD Pipeline Integration

An example of an Azure policy you can integrate with your DevOps pipeline is 

- <a href="https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/azure-policy-check-gate?view=vsts" target="_blank"><span style="color: #0066cc;" color="#0066cc">Check Gate Task</span></a> - Security and compliance assessment with Azure policies on resources that belong to the defined resource group and Azure subscription. Which is available as a release pipeline **Deploy** task.



> **Note**: You can read more about Azure Policy on the <a href="https://azure.microsoft.com/en-us/services/azure-policy/
" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy</span></a> webpage.
