This walkthrough shows how to use the Azure CLI with the Maven Plugin for Azure Web Apps (Preview) to deploy a Java Web archive file.


### Prerequisites
-  You require an Azure subscription to perform the following steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps:


1. Open Azure Cloud Shell by going to <a href="https://shell.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://shell.azure.com</span></a>, or by using the Azure Portal, and select **Bash** as the environment option.

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="The open cloud shell icon in Bash Environment is selected."></p>

2. Create a Java app by executing the Maven command in the Cloud Shell prompt to create a new app named `helloworld`: Accept the default values as you go:

    ```bash
    mvn archetype:generate -DgroupId=example.demo -DartifactId=helloworld -DarchetypeArtifactId=maven-archetype-webapp
    ```

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservices2.png" alt="Screenshot of the Open Cloud Shell icon in the Bash environment, and the maven command being run."></p>

3. Select the braces icon in Cloud Shell to open the editor. Use this code editor to open the project file **pom.xml** in the **helloworld** directory. 
 

4.  Add the following plugin definition inside the &#60build&#62 element of the pom.xml file"

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

    - RESOURCEGROUP_NAME (can be any name)
    - WEBAPP_NAME (must be a unique name)
    - REGION (your nearest datacenter location. For example, westus)
    
6.  Deploy your Java app to Azure using the following command:

    ```bash
    mvn package azure-webapp:deploy
    ```

7. After this step completes, verify deployment by opening the deployed application using the following URL in your web browser, replacing *webapp* with the name of the deployed application. For example, http://<*webapp*>.azurewebsites.net/helloworld. 

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservices3.png" alt="Hello world website displaying the text, This is the homepage for the helloworld Java App."></p>
