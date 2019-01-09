Using Resource Manager templates will make your deployments faster and more repeatable. For example, you no longer have to create a VM in the portal, wait for it to finish, then create the next VM, and so on. Resource Manager takes care of the entire deployment for you.

Here are some other benefits to consider.

* **Templates improve consistency**

    Resource Manager templates provide a common language for you and others to describe your deployments. Regardless of the tool or SDK used to deploy the template, the structure, format, and expressions inside the template remain the same.

* **Templates help express complex deployments**

    Templates enable you to deploy multiple resources in the correct order. For example, you wouldn't want to deploy a virtual machine before creating OS disk or network interface. Resource Manager maps out each resource and its dependent resources and creates dependent resources first. Dependency mapping helps ensure that the deployment is carried out in the correct order.

* **Templates reduce manual, error-prone tasks**

    Manually creating and connecting resources can be time consuming, and it's easy to make mistakes along the way. Resource Manager ensures that the deployment happens the same way every time.

* **Templates are code**

    Templates express your requirements through code. Think of a template as a type of _infrastructure as code_ that can be shared, tested, and versioned like any other piece of software. Also, because templates are code, you can create a "paper trail" that you can follow. The template code documents the deployment. Most users maintain their templates under some kind of revision control, such as Git. When you change the template, its revision history also documents how the template (and your deployment) has evolved over time.

* **Templates promote reuse**

    Your template can contain parameters that are filled in when the template runs. A parameter can define a username or password, a domain name, and so on. Template parameters enable you to create multiple versions of your infrastructure, such as staging and production, but still utilize the exact same template.

* **Templates are linkable**

    Resource Manager templates can be linked together to make the templates themselves modular. You can write small templates that each define a piece of a solution and combine them to create a complete system.

.