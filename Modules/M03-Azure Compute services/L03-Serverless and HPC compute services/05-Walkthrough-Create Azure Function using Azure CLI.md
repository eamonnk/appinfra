This walkthrough shows how to create a function from the command line or terminal. You use the Azure CLI to create a function app, which is the serverless infrastructure that hosts your function. The function code project is generated from a template by using the Azure Functions Core Tools, which is also used to deploy the function app project to Azure.

### Prerequisites

- Use Azure Cloud Shell.

- You require an Azure subscription to perform these steps. If you don't have one, you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

1. Open Azure Cloud Shell by going to https://shell.azure.com, or via the Azure Portal and selecting **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="the Open cloud shell icon in the Bash environment is selected."></p>

2. Create the local function app project by running the following command from the command line to create a function app project in the MyFunctionProj folder of the current local directory. A GitHub repo is also created in MyFunctionProj:


    ```bash
    func init MyFunctionProj
    ```

    When prompted, select a worker runtime from the following language choices: 
    - dotnet. Creates a .NET class library project (.csproj). 
    - node. Creates a JavaScript project.

3. Use the following command to navigate to the new MyFunctionProj project folder:

    ```bash
    cd MyFunctionProj
    ```

4. Create a function using the following command, which creates an HTTP-triggered function named MyHttpTrigger:


    ```bash
    func new --name MyHttpTrigger --template "HttpTrigger"
    ```

5. Update the function. By default, the template creates a function that requires a function key when making requests. To make it easier to test the function in Azure, you need to update the function to allow anonymous access. The way that you make this change depends on your functions project language. For C#:

    - Open the `MyHttpTrigger.cs` code file that is your new function. Use the following command to update the **AuthorizationLevel** attribute in the function definition to a value of anonymous, and save your changes:

    ```C#
    [FunctionName("MyHttpTrigger")]
            public static IActionResult Run([HttpTrigger(AuthorizationLevel.Anonymous, 
                "get", "post", Route = null)]HttpRequest req, ILogger log)
    ```

6. Run the function locally. The following command starts the function app, which runs using the same Azure Functions runtime that is in Azure:

    ```bash
    func host start --build
    ```

    The --build option is required to compile C# projects. 

7. Confirm the output. When the Functions host starts, it write something similar to the following output, which has been truncated for readability:

    ```bash
    
                      %%%%%%
                     %%%%%%
                @   %%%%%%    @
              @@   %%%%%%      @@
           @@@    %%%%%%%%%%%    @@@
         @@      %%%%%%%%%%        @@
           @@         %%%%       @@
             @@      %%%       @@
               @@    %%      @@
                    %%
                    %
    
    ...
    
    Content root path: C:\functions\MyFunctionProj
    Now listening on: http://0.0.0.0:7071
    Application started. Press Ctrl+C to shut down.
    
    ...
    
    Http Functions:
    
            HttpTrigger: http://localhost:7071/api/MyHttpTrigger
    
    [8/27/2018 10:38:27 PM] Host started (29486ms)
    [8/27/2018 10:38:27 PM] Job host started
    ```
    
    - Copy the URL of your **HttpTrigger** function from the runtime output, and paste it into your browser's address bar. Append the query string ?name=*yourname* to this URL, and execute the request. The following image is the response in the browser to the GET request returned by the local function.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-functions7.png" alt="Azure Function output"></p>

    Now that you have run your function locally, you can create the function app and other required resources in Azure.

8. Create a resource group. An *Azure resource group* is a logical container into which Azure resources such as function apps, databases, and storage accounts are deployed and managed. Use the following command to create the resource group az group create. 

    ```bash
    az group create --name myResourceGroup --location westeurope
    ```
    
9. Create an Azure Storage account. Functions uses a general-purpose account in Azure Storage to maintain state and other information about your functions. Create a general-purpose storage account in the resource group you created by using the **az storage account create** command.
In the following command, substitute a globally unique storage account name where you see the <*storage_name*> placeholder. Storage account names must be between 3 and 24 characters in length, and can contain numbers and lowercase letters only:

    
    ```bash
    az storage account create --name <storage_name> --location westeurope --resource-group myResourceGroup --sku Standard_LRS
    ```
    
   After the storage account has been created, the Azure CLI shows information similar to the following example:
    
    ```json
    {
      "creationTime": "2017-04-15T17:14:39.320307+00:00",
      "id": "/subscriptions/bbbef702-e769-477b-9f16-bc4d3aa97387/resourceGroups/myresourcegroup/...",
      "kind": "Storage",
      "location": "westeurope",
      "name": "myfunctionappstorage",
      "primaryEndpoints": {
        "blob": "https://myfunctionappstorage.blob.core.windows.net/",
        "file": "https://myfunctionappstorage.file.core.windows.net/",
        "queue": "https://myfunctionappstorage.queue.core.windows.net/",
        "table": "https://myfunctionappstorage.table.core.windows.net/"
      },
         ....
        // Remaining output has been truncated for readability.
    }
    ```    

10. Create a function app. You must have a function app to host the execution of your functions. The function app provides an environment for serverless execution of your function code. It lets you group functions as a logic unit for easier management, deployment, and sharing of resources. Create a function app by using the **az functionapp create** command. 

    In the following command, substitute a unique function app name where you see the <*app_name*> placeholder, and the storage account name for <*storage_name*>. The <*app_name*> is used as the default DNS domain for the function app, and so the name needs to be unique across all apps in Azure. You should also set the <*language*> runtime for your function app, from dotnet (C#) or node (JavaScript).


    ```bash
    az functionapp create --resource-group myResourceGroup --consumption-plan-location westeurope \
    --name <app_name> --storage-account  <storage_name> --runtime <language> 
    ```

       Setting the *consumption-plan-location* parameter means that the function app is hosted in a Consumption hosting plan. In this serverless plan, resources are added dynamically as required by your functions, and you only pay when functions are running.
       After the function app has been created, the Azure CLI shows information similar to the following example:

    ```json
    {
      "availabilityState": "Normal",
      "clientAffinityEnabled": true,
      "clientCertEnabled": false,
      "containerSize": 1536,
      "dailyMemoryTimeQuota": 0,
      "defaultHostName": "quickstart.azurewebsites.net",
      "enabled": true,
      "enabledHostNames": [
        "quickstart.azurewebsites.net",
        "quickstart.scm.azurewebsites.net"
      ],
       ....
        // Remaining output has been truncated for readability.
    }
    ```

11. Deploy the function app project to Azure. After the function app is created in Azure, you can use the **func azure functionapp publish** command to deploy your project code to Azure:

    ```bash
    func azure functionapp publish <FunctionAppName>
    ```

       You'll see something like the following output, which has been truncated for readability.

    ```bash
    Getting site publishing info...
    Preparing archive...
    Uploading content...
    Upload completed successfully...
    Deployment completed successfully...
    Syncing triggers...
    ```
    
    You are now ready to test your functions in Azure.

12. Test the function. Use **cURL** to test the deployed function on a Mac or Linux computer, or using Bash on Windows. Execute the following **cURL **command, replacing the < *app_name* > placeholder with the name of your function app. Append the query string &name=< *yourname* > to the URL:

    ```bash
    curl https://< app_name >.azurewebsites.net/api/MyHttpTrigger?name=< yourname >
    ```

> **Note**: remember to delete the resources if you are no longer using them.
