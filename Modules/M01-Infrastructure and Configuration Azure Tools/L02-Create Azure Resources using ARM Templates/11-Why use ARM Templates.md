Using Azure Resource Manager templates makes your deployments faster and more repeatable. For example, with templates, you do not need to create a VM in Azure portal, wait for it to finish, then create the next VM, and so on. Azure Resource Manager takes care of the entire deployment for you.

The following are benefits to using Azure Resource Manager templates.

:one: **Templates improve consistency**

Resource Manager templates provide a common language for describing your deployments. Regardless of which tool or SDK is used to deploy the template, the structure, format, and expressions inside the template remain the same.

:two: **Templates help express complex deployments**

Templates enable you to deploy multiple resources in the correct order. For example, you can create an OS Disk Image or Network Interface before you deploy a VM. Template map the dependent resources to each resource. Using the template, Azure Resource Manager begins by creating each of the dependent resources first. Dependency mapping helps ensure that your deployments occur in the correct order.

:three: **Templates reduce manual, error-prone tasks**

Manually creating and connecting resources can be time consuming, and mistakes can be made along the way. Azure Resource Manager ensures your deployments happen the same way every time.

  ![Image representing a three tier template file. An icon representing a script is shown at the top. Three arrows point outwards from the script icon. Each of the arrows points to an icon below the script icon. The first arrow points to an icon representing a SQL database, the second arrow points to an icon representing an App Service, and the third icon points to an icon representing a Virtual Machine. The SQL database and App Service icons are linked with an additional arrow, below the icons. The arrow is labelled 'reference()', to indicate that the SQL database template uses the reference function to call the App Service template. The text label 'Resource Group' is shown in the bottom right corner of the image, to indicate that all three services belong to the same resource group.](../Linked_Image_Files/3-tier-template.png)

:four: **Templates are code**

Templates allow you to define your requirements in code. Think of a template as a type of *Infrastructure as Code* that can be shared, tested, and version-controlled, just like any other piece of software. Also, because templates are code, they create a 'paper trail' which can be traced to help resolve issues. The template code acts as a record of your deployments. Most users maintain their templates under some kind of revision control, such as Git. When you change the template, its revision history also help track changes to the template (and your deployments) over time.

:five: **Templates promote reuse**

Your template can contain parameters that are assigned values when the template runs. A parameter can define a username or password, a domain name, and so on. Template parameters enable you to create and utilize the same templates across different implementations of your infrastructure, such as your staging and production environments.

:six: **Templates are linkable**

Azure Resource Manager templates can be linked together, which supports modularization. You can write small templates, each of which defines a particular piece of your solution and then combine them to create a complete system.
