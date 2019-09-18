This walkthrough shows how to create an ASP.NET Core web app, and then deploy it to Azure App Services.


### Prerequisites
You require the following items to complete these walkthrough steps:

- Visual Studio 2017. If you don't have Visual Studio 2017, you can install the Visual Studio Community edition from the <a href="https://visualstudio.microsoft.com/downloads/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Visual Studio downloads</span></a> webpage.
- An Azure subscription. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

1. In Visual Studio, create a project by selecting **File**, **New**, and then **Project**. 

2.  In the **New Project** dialog, select **Visual C#**, **Web**, and then **ASP.NET Core Web Application**.


3. Name the application **myFirstAzureWebApp**, and then select **OK**.


    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice1.png" alt="Visual Studio create new project dialogue."></p>
    
    You can deploy any type of ASP.NET Core web app to Azure. For this walkthrough, select the **Web Application** template. Ensure authentication is set to **No Authentication** and no other option is selected, and then Select **OK**.

4. To run the web app locally. from the menu, select **Debug**, **Start**, without Debugging.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice2.png" alt="Screenshot of the ASP.NET Core webpage."></p>

5. Launch the **Publish wizard** by going to **Solution Explorer**, right-clicking the **myFirstAzureWebApp** project, and then selecting **Publish**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice3.png" alt="Visual Studio Solution Explorer with project highlighted and right click context menu option, publish also highlighted."></p>

6. To open the **Create App Service** dialog, select **App Service**, and then select **Publish**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice4.png" alt="Visual Studio Publish wizard on the Pick a publish target page with App service highlighted and the Publish button also highlighted."></p>

7. Sign in to Azure by going to the **Create App Service** dialog, select **Add an account...**, and sign in to your Azure subscription. If you're already signed in, select the account you want from the drop-down. If you're already signed in, don't select  the **Create** button.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice5.png" alt="Visual Studio Publish wizard on the Create App Service page with the Add an account page highlighted."></p>

8.  Next to **Resource Group**, select **New**. Name the resource group **myResourceGroup**, and then select **OK**.

9. Next to Hosting Plan, select **New**. Use the following values, and then select **OK**
    
    - App Service Plan: **myappserviceplan**
    - Location: **your nearest datacenter**
    - Size: **Free**

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice6.png" alt="Visual Studio Publish wizard on Configure Hosting Plan page with App service Plan, Location and Size drop down boxes highlighted."></p>

 > **Note**: An App Service plan specifies the location, size, and features of the web server farm that hosts your app. You can save money when hosting multiple apps by configuring the web apps to share a single App Service plan"
    - Region (for example: North Europe, East US, or Southeast Asia) 
    - Instance size (small, medium, or large)
    - Scale count (1 to 20 instances)
    - SKU (Free, Shared, Basic, Standard, or Premium)


10. While still in the **Create App Service** dialog, enter a value for the app name, and then select **Create**.
    
> Note: The app name must be a unique value. Valid characters are a-z, 0-9, and -). Alternatively, you can accept the automatically-generated unique name. The resulting URL of the web app is http://*app_name*.azurewebsites.net, where *app_name* is your app's name.

   <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice7.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

11.  After the wizard completes, it publishes the ASP.NET Core web app to Azure, and then launches the app in the default browser. 

<p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice8.png" alt="Screenshot of the deployed application on the ASP.NET page."></p>

   The app name specified in the create and publish step is used as the URL prefix in the format http://<app_name>.azurewebsites.net. 
    
   Congratulations, your ASP.NET Core web app is running live in Azure App Service.

> **Note**: If you do not plan on using the resources, you should delete them to avoid incurring charges.
