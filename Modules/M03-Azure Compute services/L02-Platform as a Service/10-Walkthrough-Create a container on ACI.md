This walkthrough demonstrates how to use Azure CLI to create a container in Azure and make its application available with an FQDN. A few seconds after you execute a single deployment command, you can browse to the running application:

### Prerequisites
- You require an Azure subscription to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

1. Open Azure Cloud Shell by going to https://shell.azure.com, or using the Azure portal and selecting **Bash** as the environment option

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>
 
    > **Note**: You can use a local version on Azure CLI if you want, but it must be version 2.0.27 or later.

2. Create a resource group using the following command, substituting your values for the resource group name and location:


    ```bash
    az group create --name myResourceGroup --location eastus
    ```

3. Create a container, substituting your values for  the resource group name and container name. Ensure it is a unique DNS name. In the following command, we specify to open port 80 and apply a DNS name on the container:

    ```bash
    az container create --resource-group myResourceGroup --name mycontainer --image microsoft/aci-helloworld --dns-name-label aci-demo --ports 80
    ```

3. Verify the container status by running the following command, again substituting your values where appropriate:


    ```bash
    az container show --resource-group myResourceGroup --name mycontainer --query "{FQDN:ipAddress.fqdn,ProvisioningState:provisioningState}" --out table
    
    ```

4. If the container's *ProvisioningState* is **Succeeded**, navigate to its FQDN in your browser. If you see a webpage similar to the follow example, congratulations! You've successfully deployed an application running in a Docker container to Azure.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-containertoaci1.png" alt="Screen capture of the Welcome to Azure Container Instances webpage."></p>

> Note: You can check the container in the portal if you want. If you are finished using the resources in Azure, delete it to ensure you do not incur costs.
