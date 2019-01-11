In this walkthrough we will deploy a custom Docker image running a Go application to Web App for Containers


> Note: you require an Azure subscription to be able to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> page.

1. Open Azure Cloud Shell by going to https://shell.azure.com or via the Azure Portal and select **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>

2. Configure a deployment user by running the command below, replacig <username> and <password> (including brackets) with a new user name and password. The user name must be unique within Azure. The password must be at least eight characters long, with two of the following three elements: letters, numbers, symbols. 
    
    > **Note**: This deployment user is required for FTP and local Git deployment to a web app. The user name and password are account level. They are different from your Azure subscription credentials. 

    ```bash
    az webapp deployment user set --user-name <username> --password <password>
    ```

    You should get a JSON output, with the password shown as null. If you get a 'Conflict'. Details: 409 error, change the username. If you get a 'Bad Request'. Details: 400 error, use a stronger password.

3. Create a resource group in Azure by Create a resource group, using the command below and substituing the reource gorup name value for one of your own choice and the location to a datacenter near you.


    ```cli
    az group create --name myResourceGroup --location "West Europe"
    
    ```

4. Create an Azure App Service plan by running the command below, it creates an App Service plan named *myAppServicePlan* in the *Basic* pricing tier, `--sku B1` and in a Linux container, `--is-linux`.

    ```bash
    az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku B1 --is-linux
    
    ```

5. Create a web app in your App service plan by running the below command, replacing  <app name > with  a globally unique name, and also the resource group and App Service plan names to values you crated earlier. This command points to the public Docker Hub image `microsoft/azure-appservices-go-quickstart`.

    ```bash
    az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name <app name> --deployment-container-image-name microsoft/azure-appservices-go-quickstart
    
    ```
    When the web app has been created, the Azure CLI shows output similar to the following example:
    ```json
    {
      "availabilityState": "Normal",
      "clientAffinityEnabled": true,
      "clientCertEnabled": false,
      "cloningInfo": null,
      "containerSize": 0,
      "dailyMemoryTimeQuota": 0,
      "defaultHostName": "<app name>.azurewebsites.net",
      "deploymentLocalGitUrl": "https://<username>@<app name>.scm.azurewebsites.net/<app name>.git",
      "enabled": true,
      < JSON data removed for brevity. >
    }
    ```

6. Browse to the app http://<app_name>.azurewebsites.net/hello

Congratulations! You've deployed a custom Docker image running a Go application to Web App for Containers
