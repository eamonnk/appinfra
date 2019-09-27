
You can deploy Chef on Microsoft Azure from the Azure Marketplace using the Chef Automate image. *Chef Automate* is a Chef product that allows you to package and test your applications, and provision and update your infrastructure. With Chef you can manage changes to your applications and infrastructure using compliance and security checks, and dashboards that give you visibility into your entire stack.

The Chef Automate image is available on the Azure Chef Server and has all the functionality of the legacy Chef Compliance server. You can build, deploy, and manage your applications and infrastructure on Azure. Chef Automate is available from the Azure Marketplace, and you can try it out with a free 30-day license. You can deploy it in Azure straight away.

### Chef Automate structure and function

Chef Automate integrates with the open-source products Chef, InSpec, Habitat, and associated tools, including chef-client and ChefDK. The following image provides an overview of the structure of Chef Automate, and how it functions.

<p style="text-align:center;"><img src="../Linked_Image_Files/chefautomate.png" alt="The high-level Chef Automate architecture contains a box labeled Collaborate, which sits on top of three boxes labeled Build, deploy and Manage. These three boxes are over a box labeled OSS Automation Engines, which in turn sits over boxes labeled Chef, habitat and InSpec."></p>

- Habitat. Habitat is an open-source project that offers an entirely new approach to application management. It makes the application and its automation the unit of deployment by creating platform-independent build artifacts that can run on traditional servers and virtual machines (VMs). Applications can be wrapped in a lightweight “habitat” (the runtime environment). Habitats can be exported into your preferred container platform, enabling you to deploy your applications in any environment. Identifying the habitat as a container, a bare metal machine, or platform as a service (PaaS) is no longer necessary, which places less constraints on the application.

For more information about Habitat, see the <a href="https://docs.microsoft.com/en-us/azure/chef/chef-habitat-overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Use Habitat to deploy your application to Azure</span></a> page.

- InSpec. InSpec is a free and open-source framework for testing and auditing your applications and infrastructure. InSpec works by comparing the actual state of your system with the desired state that you define in easy-to-read and easy-to-write InSpec code. InSpec detects violations and displays its findings as a report, but InSpec keeps you in control of remediation.

You can use InSpec to validate the state of your VMs running in Azure. You can also use InSpec to scan and validate the state of resources and resource groups inside a subscription.

More information about InSpec is available at <a href="https://docs.microsoft.com/en-us/azure/chef/chef-inspec-overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Use InSpec for compliance automation of your Azure infrastructure</span></a>.
