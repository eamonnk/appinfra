

Chef is available to deploy on Azure from the **Azure Marketplace** using the **Chef Automate** image. 

**Chef Automate** is a Chef product that allows you to package and test your applications, provision and update your infrastructure, and manage it all with compliance and security checks and dashboards that give you visibility into your entire stack.

The Chef Automate image available on Azure Chef Server and has all the functionality of the legacy Chef Compliance server and allows you to build, deploy and manage your applications and infrastructure on Azure. It is available from the Azure Marketplace to try with a free 30 day license. It is available to deploy in Azure straight straight away.


### Chef Automate structure and Function
Chef Automate integrates with the open-source products **Chef, InSpec** and **Habitat** and associated tools, chef-client, ChefDK etc. An overview of Chef Automate and how it is structured and how it functions is displayed in the following image below:

<p style="text-align:center;"><img src="../Linked_Image_Files/chefautomate.png" alt="Diagram of the high-level Chef Automate architecture,containing a box labelled Collaborate, which site sover three boxes labelled, Build, deploy and Manage, which sit over a box labelled OSS Automation Engines, which tin turn sits over boxes for Chef, habitat and InSpec."></p>

- **Habitat** - <a href="https://docs.microsoft.com/en-us/azure/chef/chef-habitat-overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Habitat</span></a> is an open-source project that offers an entirely new approach to application management. Habitat makes the application and its automation the unit of deployment by creating platform-independent build artifacts that can be run on traditional servers and virtual machines, or exported into your preferred container platform, letting you deploy your applications in any environment. When applications are wrapped in a lightweight “habitat,” the runtime environment, whether it is a container, bare metal, or PaaS, is no longer the focus and does not constrain the application.

- **Inspec** - <a href="https://docs.microsoft.com/en-us/azure/chef/chef-inspec-overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Inspec</span></a> is a free and open-source framework for testing and auditing your applications and infrastructure. InSpec works by comparing the actual state of your system with the desired state that you express in easy-to-read and easy-to-write InSpec code. InSpec detects violations and displays findings in the form of a report, but puts you in control of remediation. You can use InSpec to validate the state of your virtual machines running in Azure. You can also use InSpec to scan and validate the state of resources and resource groups inside of a subscription.

