In App Service, an app runs in an App Service plan. An App Service plan defines a set of compute resources for a web app to run. These compute resources are analogous to the *server farm* in conventional web hosting. One or more apps can be configured to run on the same computing resources (or in the same App Service plan).


When you create an App Service plan in a certain region (for example, West Europe), a set of compute resources is created for that plan in that region. Whatever apps you put into this App Service plan run on these compute resources as defined by your App Service plan. 

Each App Service plan defines:
- Region (West US, East US, etc.)
- Number of VM instances
- Size of VM instances (Small, Medium, Large)
- Pricing tier (Free, Shared, Basic, Standard, Premium, PremiumV2, Isolated, Consumption)

### Pricing Tiers
The pricing tier of an App Service plan determines what App Service features you get and how much you pay for the plan. There are a few categories of pricing tiers:
- **Shared compute**: *Free* and *Shared*, the two base tiers, runs an app on the same Azure VM as other App Service apps, including apps of other customers. These tiers allocate CPU quotas to each app that runs on the shared resources, and the resources **cannot** scale out.
- **Dedicated compute**: The *Basic*, *Standard*, *Premium*, and *PremiumV2* tiers run apps on dedicated Azure VMs. Only apps in the same App Service plan share the same compute resources. The higher the tier, the more VM instances are available to you for scale-out.
- **Isolated**: This tier runs dedicated Azure VMs on dedicated *Azure Virtual Networks*, which provides network isolation on top of compute isolation to your apps. It provides the maximum scale-out capabilities.
- **Consumption**: This tier is only available to *function apps*. It scales the functions dynamically depending on workload. 
- 
- 
- > **Note**: More general details are available on the <a href="https://docs.microsoft.com/en-us/azure/app-service/overview-hosting-plans?toc=%2fazure%2fapp-service%2fcontainers%2ftoc.json" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure App Service plan overview</span></a> page.