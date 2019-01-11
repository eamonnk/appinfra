This walkthrough shows how to create a an ASP.NET Core web app and deploy it to Azure App Services


### Prerequisites
You require the following to be able to complete these walkthrough steps
- **Visual Studio 2017** - If you don't have VS2017 you can install Visual Studio Community edition from the <a href="https://visualstudio.microsoft.com/downloads/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Visual Studio downloads</span></a> page.
- An **Azure subscription** - If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> page.

### Steps

1. In Visual Studio, create a project by selecting File > New > Project. 

2.  In the New Project dialog, select Visual C# > Web > ASP.NET Core Web Application.


3. Name the application **myFirstAzureWebApp**, and then select **OK**.


    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice1.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>
    
    You can deploy any type of ASP.NET Core web app to Azure. For this walkthrough, select the *Web Application* template, and make sure authentication is set to **No Authentication** and no other option is selected, then Select **OK**.

4. From the menu, select **Debug** > **Start** without Debugging to run the web app locally.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice2.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

5. Launch the **publish** wizard by going to **Solution Explorer**, right-clicking the **myFirstAzureWebApp** project and selecting **Publish**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice3.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

6. The publish wizard is automatically launched. Select App Service > Publish to open the Create App Service dialog.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice4.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

7. Sign in to Azure by going to the **Create App Service** dialog, click **Add an account...**, and sign in to your Azure subscription. If you're already signed in, select the account you want from the dropdown. If you're already signed in, **don't** select **Create** yet.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice5.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

8.  Create a resource group > Next to **Resource Group**, select **New**> and Name the resource group myResourceGroup and select **OK**.

9. Create an App Service plan > Next to Hosting Plan, select **New** and using the following values and then select **OK**
    
    - App Service Plan:  < myappserviceplan >
    - Location: < your nearest datacenter >
    - Size: < Free >

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice6.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

    *Note*: An App Service plan specifies the location, size, and features of the web server farm that hosts your app. You can save money when hosting multiple apps by configuring the web apps to share a single App Service plan. 
    - Region (for example: North Europe, East US, or Southeast Asia) 
    - Instance size (small, medium, or large)
    - Scale count (1 to 20 instances)
    - SKU (Free, Shared, Basic, Standard, or Premium)


10. Create and publish the web app whil still in the **Create App Service** dialog enter a value for the app name and select **Create**
    
    - App name: < must be a unique valie i.e. (valid characters are a-z, 0-9, and -), or accept the automatically generated unique name. The resulting URL of the web app is http://<app_name>.azurewebsites.net, where <app_name> is your app name.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice7.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

11.  Once the wizard completes, it publishes the ASP.NET Core web app to Azure, and then launches the app in the default browser. 

<p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-aspnetcoreinappservice8.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

    The app name specified in the create and publish step is used as the URL prefix in the format http://<app_name>.azurewebsites.net. Congratulations, your ASP.NET Core web app is running live in Azure App Service.

> **Note**: If you do not plan on using the resources you should delete them to avoid incurring charges.