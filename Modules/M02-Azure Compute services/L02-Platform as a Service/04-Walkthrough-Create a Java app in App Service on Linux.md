This walkthrough shows how to use the Azure CLI with the Maven Plugin for Azure Web Apps (Preview) to deploy a Java web archive (WAR) file.

> Note: you require an Azure subscription to be able to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> page.

Steps:
1. Open Azure Cloud Shell by going to https://shell.azure.com or via the Azure Portal and select **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>

2. Create a Java App by executing the below **Maven** command in the Cloud Shell prompt to create a new app named `helloworld`: Accept the defaul values as you go.

    ```bash
    mvn archetype:generate -DgroupId=example.demo -DartifactId=helloworld -DarchetypeArtifactId=maven-archetype-webapp
    ```

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservices2.png" alt="Open cloud shell icon in Bash Environment and maven command being run."></p>

3. Click the curly brackets icon in cloud shell to open the editor, and use this code editor in the Cloud Shell to open up the project **pom.xml** file in the **helloworld** directory. 
 

4.  Add the following plugin definition inside the <build> element of the pom.xml file.

    ```bash
    <plugins>
        <!--*************************************************-->
        <!-- Deploy to Tomcat in App Service Linux           -->
        <!--*************************************************-->
    
        <plugin>
            <groupId>com.microsoft.azure</groupId>
            <artifactId>azure-webapp-maven-plugin</artifactId>
            <version>1.4.0</version>
            <configuration>
    
                <!-- App information -->
                <resourceGroup>${RESOURCEGROUP_NAME}</resourceGroup>
                <appName>${WEBAPP_NAME}</appName>
                <region>${REGION}</region>
    
                <!-- Java Runtime Stack for App on Linux-->
                <linuxRuntime>tomcat 8.5-jre8</linuxRuntime>
    
            </configuration>
        </plugin>
    </plugins>
    ```

5. Update the following placeholders in the plugin configuration:

    - RESOURCEGROUP_NAME < can be anyu name >
    - WEBAPP_NAME < must be unique name >
    - REGION < your nearest datacernmer locations i.e. westus>
    
6.  Deploy your Java app to Azure using the following command:

    ```bash
    mvn package azure-webapp:deploy
        ```

7. Ince completed verify deployment by going to the deployed application using the following URL in your web browser, for example http://<webapp>.azurewebsites.net/helloworld. 

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservices3.png" alt="Web browser accessing the jav app and visible text saying This is the homepage for thr helloworld Java App."></p>
