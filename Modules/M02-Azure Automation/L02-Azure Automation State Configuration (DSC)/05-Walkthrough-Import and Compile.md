

After creating your DSC configuration file, you must import the file and compile it to the DSC pull server. Compiling will create the MOF file. Read more about this at [Compiling a DSC Configuration with the Azure portal](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-the-azure-portal).



### Import and compile configurations

To import and compile a configuration, complete the following high-level steps:

1. Create a configuration file by creating a file on your local machine. Then, copy and paste the following PowerShell code into the file, and name it **LabConfig.ps1**. This script configuration will ensure the IIS web-server role is installed on the servers:

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

2.  In Azure Automation, account under **Configuration Management** > **State configuration (DSC)**, select the  **Configurations** tab, and then select **+Add**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc3.png" alt="Screenshot of Azure Automation pane, highlighting Configuration Management, State Configuration, Configurations tab and the + Add button"></p>

3. Point to the configuration file you want to import, and then select **OK**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc4.png" alt="Screenshot of the Import Configuration pane. In the Import dialog box, the Configuration file is set to LabConfig.ps1."></p>

4. Once imported double click the file, select **Compile**, and then confirm by selecting **Yes**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc5.png" alt="Screenshot of the LabConfig properties pane with the Compile button selected."></p>

5. Once compiled, verify that the file has a status of completed.
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc6.png" alt="Screenshot of the LabConfig properties pane. Under Compilation jobs, a status of completed displays."></p>


> **Note**: If you prefer, you can also use the **PowerShell Start-AzAutomationDscCompilationJob** cmdlet. More information about this method is available at <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-windows-powershell" target="_blank"><span style="color: #0066cc;" color="#0066cc">Compiling a DSC Configuration with Windows PowerShell</span></a>.
