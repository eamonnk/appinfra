This walkthrough shows how to use the Azure CLI to create a container in Azure and make its application available with a fully qualified domain name (FQDN). A few seconds after you execute a single deployment command, you can browse to the running application:

> Note: you require an Azure subscription to be able to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> page.

Steps:
1. Open Azure Cloud Shell by going to https://shell.azure.com or via the Azure Portal and select **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>
 
    > **Note**: You can use a local version on Azure CLI if you wish. It just needs to be version 2.0.27 or later.

2. Create a resource group using the below command, substituting your vales for resource group name and location


    ```bash
    az group create --name myResourceGroup --location eastus
    ```

3. Create a container, substituting your values for resource group name and container name, and also ensure it is a unique dns name. We specify to open port 80 to open and a dns name on the container

    ```bash
    az container create --resource-group myResourceGroup --name mycontainer --image microsoft/aci-helloworld --dns-name-label aci-demo --ports 80
    ```

3. check the container status by running the below command, again substituting your values where appropriate.


    ```bash
    az container show --resource-group myResourceGroup --name mycontainer --query "{FQDN:ipAddress.fqdn,ProvisioningState:provisioningState}" --out table
    
    ```

4. If the container's *ProvisioningState* is **Succeeded**, navigate to its FQDN in your browser. If you see a web page similar to the below, congratulations! You've successfully deployed an application running in a Docker container to Azure.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-containertoaci1.png" alt="Web browser accessing the jav app and visible text saying This is the homepage for thr helloworld Java App."></p>

> **Note**: You cna check the container int he portal if you wish and also, if you are finished using the resources in Azure, ensure you delete it to ensure you do not incur costs.
