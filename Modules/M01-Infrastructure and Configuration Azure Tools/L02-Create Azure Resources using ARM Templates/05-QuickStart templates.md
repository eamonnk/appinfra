*Azure Quickstart Templates* are Azure Resource Manager Templates that have been created by the Azure development community.

> :information_source: You can access Quickstart Templates via the [Azure Quickstart Templates](https://azure.microsoft.com/en-us/resources/templates/) page and from the [GitHub Azure Quickstart Template](https://github.com/Azure/azure-quickstart-templates) page.

There are many templates to provide you with everything you need to deploy your solution. Some templates may serve as a suitable starting point for developing your own templates. You can learn how to author and structure your own templates by studying existing templates.

### Discover the Azure Quickstart Template gallery

Imagine a scenario where you need a Resource Manager template that can bring up a basic Virtual Machine (VM) configuration. You need the template to include a VM, basic network settings, and storage.

The following steps are a useful guide to help you find a suitable template.

1. Start by browsing to the [Quickstart template gallery](https://azure.microsoft.com/resources/templates?azure-portal=true), to see what's available.

    You see a number of popular and recently updated templates. These templates work with both Azure resources and other popular software packages.

    ![Screenshot of a portion of the Azure Quickstart template gallery web page.](../Linked_Image_Files/gallery-homepage.png)

2. Let's say you come across the [Deploy a simple Windows VM](https://azure.microsoft.com/resources/templates/101-vm-simple-windows?azure-portal=true) template.

    ![Screenshot of the gallery page for a Windows VM template](../Linked_Image_Files/gallery-page-windows.png)

    Let's take a closer look to see what this template accomplishes.

    > :information_source: Note that the **Deploy to Azure** button allows you to deploy the template directly through the Azure Portal, if you wish.

3. Choose **Browse on GitHub** to navigate to the template's source code on GitHub.

    You see the following:

    ![Screenshot of the GitHub README for the Resource Manager template](../Linked_Image_Files/github-page-windows.png)

    > :information_source: Note that the **Deploy to Azure** button allows you to deploy the template directly through the Azure portal, just like on the gallery page.

4. Choose **Visualize** to navigate to the **Azure Resource Manager Visualizer**.

    This shows you the resources that make up the deployment, including a VM, a storage account, and network resources.

    You can rearrange the resources, if you need to or zoom in an out.

    ![Screenshot of the Azure Resource Manager Visualizer showing Azure resources](../Linked_Image_Files/armviz-windows.png)

5. Select the **Virtual Machine** resource labeled **SimpleWinVM**.

    This displays the source code that defines the VM resource.

    ![Screenshot of the Azure Resource Manager Visualizer showing the template's source code](../Linked_Image_Files/armviz-vm-windows.png)

    Review the code briefly shows that:

    - The resource's type is `Microsoft.Compute/virtualMachines`.
    - It's location, or Azure region, comes from the template parameter named `location`.
    - The VM's size is **Standard_A2**.
    - The computer name is read from a template variable and the username and password for the VM are read from template parameters.

In practice, you might review the `README.md` file on GitHub and further inspect the source code to see whether this template suits your needs.
