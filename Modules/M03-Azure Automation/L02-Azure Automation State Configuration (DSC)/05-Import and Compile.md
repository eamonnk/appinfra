

After creating your DSC configuration file, you must import the file and [compile it to the DSC pull server](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-the-azure-portal). Compiling will create the MOF file.



### Import and Compile configurations

1. Create a configuration file by creating a file on your local machine and copying and pasting the below powershell code into the file and name it `LabConfig.ps1`. This script configuration will ensure the Web-Server role, IIS, is installed on the servers.

    ```powershell
    configuration LabConfig 
     { 
         Node WebServer 
         { 
             WindowsFeature IIS 
             { 
                 Ensure = 'Present' 
                 Name = 'Web-Server' 
                 IncludeAllSubFeature = $true 
             } 
         } 
    } 
    ```

2.  In Azure Automation account under **Configuration Management** > **State configuration (DSC)** click the  **Configurations** tab, then click **+Add**

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc3.png" alt="Screenshot of Azure Automation pane highlighting Configuration Management, State Configuration, Configurations tab and then the + Add button"></p>

3. Point to the configuration file you wish to import and click **OK**

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc4.png" alt="Screenshot of the Import Configuration pane. In the Import dialog box, the Configuration file is set to LabConfig.ps1."></p>

34. Once imported double clkick the file and click **Compile**, and confirm by clicking **Yes**

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc5.png" alt="Screenshot of the LabConfig properties pane where the Compile button is highlighted."></p>

5. Once compiled it has a status of completed
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc6.png" alt="Screenshot of the LabConfig properties pane where the compilation jobs dashboard lists a status of complete."></p>


> **Note**:If you prefer, you can also <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-windows-powershell" target="_blank"><span style="color: #0066cc;" color="#0066cc">use the PowerShell Start-AzAutomationDscCompilationJob</span></a> cnmdlet.



