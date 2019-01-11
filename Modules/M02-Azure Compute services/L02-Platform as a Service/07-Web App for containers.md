Azure App services also supports the deployment of containers. This specific service container hosting service offering in Azure App Service, is often referred to as Web App for containers.

Web App for Containers from Azure App Service allows customers to use their own containers and deploy them to App Service as a web app. Similar to the Web App solution, Web App for Containers eliminates time-consuming infrastructure management tasks during container deployment, updating, and scaling to help developers focus on coding and getting their apps in front of more end users faster. Furthermore, it provides integrated CI/CD capabilities with DockerHub, Azure Container Registry, and VSTS, as well as built-in staging, rollback, testing-in-production, monitoring, and performance testing capabilities to boost developer productivity.

For Operations, Web App for Containers also provides rich configuration features so developers can easily add custom domains, integrate with AAD authentication, add SSL certificates and more—all crucial to web app development and management. It is an ideal environment to run web apps that do not require extensive infrastructure control.
Web App for containers.

Web App for containers supports both Linux or Windows (in preview) containers.

Web App for containers provides the following features:
- Deploy containerized applications using Docker Hub, Azure Container Registry, or private registries.
- Incrementally deploy apps into production with deployment slots and slot swaps.
- Scale out automatically with auto-scale.
- Enable application logs and use the App Service Log Streaming feature to see logs from your application.
- Use PowerShell and Win-RM to remotely connect directly into your containers.


### Walkthrough - Deploy a Docker/Go web app in Web App for Containers

1. Open Azure Cloud Shell by going to https://shell.azure.com or via the Azure Portal and select **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>

2. Configure a deployment user by running the command below, replacig < username > and < password > (including brackets) with a new user name and password. The user name must be unique within Azure. The password must be at least eight characters long, with two of the following three elements: letters, numbers, symbols. 
    
    > **Note**: This deployment user is required for FTP and local Git deployment to a web app. The user name and password are account level. They are different from your Azure subscription credentials. 

    ```bash
    az webapp deployment user set --user-name <username> --password <password>
    ```

    You should get a JSON output, with the password shown as null. If you get a 'Conflict'. Details: 409 error, change the username. If you get a 'Bad Request'. Details: 400 error, use a stronger password.

3. Create a resource group in Azure by Create a resource group, using the command below and substituting the resource group name value for one of your own choice and the location to a datacenter near you.


    ```cli
    az group create --name myResourceGroup --location "West Europe"
    
    ```

4. Create an Azure App Service plan by running the command below, it creates an App Service plan named *myAppServicePlan* in the *Basic* pricing tier, `--sku B1` and in a Linux container, `--is-linux`.

    ```bash
    az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku B1 --is-linux
    
    ```

5. Create a web app in your App service plan by running the below command, replacing  < app name > with  a globally unique name, and also the resource group and App Service plan names to values you crated earlier. This command points to the public Docker Hub image `microsoft/azure-appservices-go-quickstart`.

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
      "defaultHostName": "< app name >.azurewebsites.net",
      "deploymentLocalGitUrl": "https://< username > @< app name >.scm.azurewebsites.net/< app name >.git",
      "enabled": true,
      < JSON data removed for brevity. >
    }
    ```

6. Browse to the app `http://< app_name >.azurewebsites.net/hello`

Congratulations! You've deployed a custom Docker image running a Go application to Web App for Containers
