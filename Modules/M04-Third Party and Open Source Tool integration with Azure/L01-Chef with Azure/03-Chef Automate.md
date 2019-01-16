Chef is available to deploy on Azure from the [Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/chef-software.chef-automate?tab=Overview) using the *Chef Automate* image.

Chef Automate is a Chef product that allows you to package and test your applications. With Chef Automate you can provision and update your infrastructure, and manage it with compliance and security checks and dashboards that give you visibility into your entire stack.

The Chef Automate image available from Azure Marketplace includes Chef Server. It provides all the functionality of the legacy Chef Compliance server and allows you to build, deploy and manage your applications and infrastructure on Azure. The Chef Automate image on Azure Marketplace is available to try without a license for up to 30 days. Using the image beyond the 30 day trail period requires a software license from Chef.

### Chef Automate structure and function

Chef Automate integrates with the open-source products *Chef*, *InSpec* and *Habitat*, as well as associated tools, such as *Chef-client*, *ChefDK*, etc. The following image provides an overview of Chef Automate, how it is structured, and how it functions.

<p style="text-align:center;"><img src="../Linked_Image_Files/chefautomate.png" alt="Diagram representing a high-level overview of the Chef Automate architecture. The diagram shows three rows. Each row contains different components of the Chef Automate architecture. Collectively, the rows and their contents illustrate the various components that comprise the Chef Automate architecture."></p>

- [Habitat](https://docs.microsoft.com/en-us/azure/chef/chef-habitat-overview) is an open-source project that offers a new approach to application management. Habitat makes the application and its automation the unit of deployment. Habitat implements this novel approach by creating platform-independent build artifacts. Artifacts can run on traditional servers and virtual machines, or be exported into your preferred container platform, which allows you to deploy your applications in any environment. Applications are wrapped in a lightweight 'habitat', so that the runtime environment, whether it is a container, bare metal, or PaaS, is no longer the main focus. The result is that the runtime environment does not constrain the application.

- [InSpec](https://docs.microsoft.com/en-us/azure/chef/chef-inspec-overview) is a free and open-source framework for testing and auditing your applications and infrastructure. InSpec works by comparing the actual state of your system with the desired state. You can define desired states in easy-to-read and easy-to-write InSpec code. InSpec detects violations and displays its findings in the form of reports, but InSpec puts you in control of remediation. You can use InSpec to validate the state of the virtual machines you have running in Azure. You can also use InSpec to scan and validate the state of resources and resource groups inside of a subscription.

> :information_source: *Habitat* and *InSpec* are two open-source products that are integrated into the Chef Automate image available from Azure Marketplace.
>
> - Habitat makes the application and its automation the unit of deployment, by allowing you to create platform-independent build artifacts called 'habitats' for your applications.
>
> - InSpec allows you to define desired states for your applications and infrastructure. InSpec can conduct audits to detect violations against your desired state definitions, and generate reports from its audit results.
