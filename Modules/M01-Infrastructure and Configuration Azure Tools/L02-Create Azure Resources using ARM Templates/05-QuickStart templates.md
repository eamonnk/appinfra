**What are Azure Quickstart templates?**

*Azure Quickstart templates* are Resource Manager templates provided by the Azure community. Quickstart templates are accessible from <a href="https://azure.microsoft.com/en-us/resources/templates/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://azure.microsoft.com/en-us/resources/templates/</span></a> or <a href="https://github.com/Azure/azure-quickstart-templates" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/Azure/azure-quickstart-templates</span>.</a>

Many templates provide everything you need to deploy your solution, while others might serve as a starting point for your template. Either way, you can study these templates to learn how to best author and structure your own templates.

**Discover what's in the Quickstart template gallery**

Let's say you want to find a Resource Manager template with a basic VM configuration, preferably one that includes a VM, basic network settings, and storage. 

1. You could start by browsing to the [Azure Quickstart Templates gallery](https://azure.microsoft.com/resources/templates?azure-portal=true) to see what's available. In the gallery you will find a number of popular and recently updated templates. These templates work with both Azure resources and popular software packages.

    ![Screenshot of the Most popular section of the Azure Quickstart template gallery webpage.](../Linked_Image_Files/gallery-homepage.png)

2. Let's say you come across the <a href="https://azure.microsoft.com/resources/templates/101-vm-simple-windows?azure-portal=true" target="_blank"><span style="color: #0066cc;" color="#0066cc">Deploy a simple Windows VM</span></a> template.

    ![Screenshot of the Deploy a simple Windows VM page](../Linked_Image_Files/gallery-page-windows.png)

    > Note: The **Deploy to Azure** button enables you to deploy the template directly through the Azure portal if you wish.

    Let's take a closer look to see what this template accomplishes:

3. Click **Browse on GitHub** to navigate to the template's source code on GitHub.

    ![Screenshot of the GitHub README for the Resource Manager template](../Linked_Image_Files/github-page-windows.png)

    The **Deploy to Azure** button enables you to deploy the template directly through the Azure portal, just like you saw on the gallery page.

4. Click **Visualize** to navigate to the **Azure Resource Manager Visualizer**.

    ![The Azure Resource Manager Visualizer displaying Azure resources.](../Linked_Image_Files/armviz-windows.png)

    You can see the resources that make up the deployment, including a VM, a storage account, and network resources.

    Use your mouse to arrange the resources. You can also use your mouse's scroll wheel to zoom in an out.

5. Click on the VM resource labeled **SimpleWinVM**.

    ![The Azure Resource Manager Visualizer displays the template's source code.](../Linked_Image_Files/armviz-vm-windows.png)

    From here you can see the source code that defines the VM resource.

6. After briefly reviewing it, you see that:

    * The resource's type is `Microsoft.Compute/virtualMachines`.
    * It's location, or Azure region, comes from the template parameter named `location`.
    * The VM's size is **Standard_A2**.
    * The computer name is read from a template variable, and the username and password for the VM are read from template parameters.

You might then review the **README** file on GitHub, and further inspect the source code to see whether the template suits your needs.
