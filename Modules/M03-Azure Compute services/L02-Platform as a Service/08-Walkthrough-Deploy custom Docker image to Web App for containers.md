In this walkthrough you will deploy a custom Docker image running a Go application to Web App for Containers.


### Prerequisites
- You require need an Azure subscription to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

1. Open Azure Cloud Shell by going to https://shell.azure.com, or by using the Azure portal and selecting **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>

2. Run the following command to configure a deployment user, replacing <*username*> and <*password*> (including brackets) with a new user name and password. The user name must be unique within Azure, and the password must be at least eight characters long with two of the following three elements: letters, numbers, symbols:
    
    > **Note**: This deployment user is required for FTP and local Git deployment to a web app. The user name and password are account level. They are different from your Azure subscription credentials. 

    ```bash
    az webapp deployment user set --user-name <*username*> --password <*password*>
    ```

    You should get a JSON output, with the password shown as null. If you get a 'Conflict'. Details: 409 error, change the username. If you get a 'Bad Request'. Details: 400 error, use a stronger password.

3. Create a resource group in Azure by using the  following command and substituting the resource group name value for one of your own choice, and the location to a datacenter near you:


    ```cli
    az group create --name myResourceGroup --location "West Europe"
    
    ```

4. Create an Azure App Service plan by running the  following command, which creates an App Service plan named *myAppServicePlan* in the *Basic* pricing tier:

    ```bash
    az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku B1 --is-linux
    
    ```

5. Run the following command to create a web app in your App service plan, replacing  <*app name*> with a globally unique name, and the resource group and App Service plan names to values you created earlier. This command points to the public Docker Hub image:
 
    ```bash
    az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name < app name > --deployment-container-image-name microsoft/azure-appservices-go-quickstart
    
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

6. Browse to the app http://<*app_name*>.azurewebsites.net/hello.

Congratulations! You've deployed a custom Docker image running a Go application to Web App for Containers.
