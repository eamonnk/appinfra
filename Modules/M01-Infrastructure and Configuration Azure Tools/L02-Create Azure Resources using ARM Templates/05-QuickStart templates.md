**What are Azure Quickstart templates?**

Azure Quickstart templates are Resource Manager templates that are provided by the Azure community. Quickstart templates are accessible via <a href="https://azure.microsoft.com/en-us/resources/templates/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://azure.microsoft.com/en-us/resources/templates/</span></a> or <a href="https://github.com/Azure/azure-quickstart-templates" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/Azure/azure-quickstart-templates</span>.</a>

Many templates provide everything you need to deploy your solution. Others might serve as a starting point for your template. Either way, you can study these templates to learn how to best author and structure your own templates.

**Discover what's on the Quickstart template gallery**

Let's say you want to find a Resource Manager template that brings up a basic VM configuration, one that includes a VM, basic network settings, and storage.

1. Start by browsing to the [Quickstart template gallery](https://azure.microsoft.com/resources/templates?azure-portal=true) to see what's available.

    You see a number of popular and recently updated templates. These templates work with both Azure resources and popular software packages.

    ![A portion of the Azure Quickstart template gallery web page.](../Linked_Image_Files/gallery-homepage.png)

2. Let's say you come across the <a href="https://azure.microsoft.com/resources/templates/101-vm-simple-windows?azure-portal=true" target="_blank"><span style="color: #0066cc;" color="#0066cc">Deploy a simple Windows VM</span></a> template.

    ![The gallery page for a Windows VM template](../Linked_Image_Files/gallery-page-windows.png)

    Let's take a closer look to see what this template accomplishes.

    > Note: The **Deploy to Azure** button enables you to deploy the template directly through the Azure portal if you wish.

3. Click **Browse on GitHub** to navigate to the template's source code on GitHub.

    You see this.

    ![The GitHub README for the Resource Manager template](../Linked_Image_Files/github-page-windows.png)

    The **Deploy to Azure** button enables you to deploy the template directly through the Azure portal, just like you saw on the gallery page.

4. Click **Visualize** to navigate to the **Azure Resource Manager Visualizer**.

    You see the resources that make up the deployment, including a VM, a storage account, and network resources.

    You can use your mouse to arrange the resources. You can also use your mouse's scroll wheel to zoom in an out.

    ![The Azure Resource Manager Visualizer showing Azure resources visually](../Linked_Image_Files/armviz-windows.png)

5. Click on the **Virtual Machine** resource labeled **SimpleWinVM**.

    You see the source code that defines the VM resource.

    ![The Azure Resource Manager Visualizer showing the template's source code](../Linked_Image_Files/armviz-vm-windows.png)

    Review it briefly and you see that:

    * The resource's type is `Microsoft.Compute/virtualMachines`.
    * It's location, or Azure region, comes from the template parameter named `location`.
    * The VM's size is **Standard_A2**.
    * The computer name is read from a template variable and the username and password for the VM are read from template parameters.

In practice, you might review the **README.md** file on GitHub and further inspect the source code to see whether this template suits your needs.
