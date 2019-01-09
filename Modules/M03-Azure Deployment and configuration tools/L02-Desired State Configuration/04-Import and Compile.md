

After creating your DSC configuration file, you must import the file and [compile it to the DSC pull server](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-the-azure-portal). Compiling will create the MOF file.

![Screenshot of the Import Configuration and LabConfig dialog boxes. In the Import dialog box, the Configuration file is set to LabConfig.ps1. An arrow points to the LabConfig dialog box, where the Compile button is circled. A Yes button is selected, and an arrow points to the Deployments to Pull Server section.]( ../../Linked_Image_Files/2.3.2.png)


<table border="0" cellpadding="0">
<tbody>
<tr>
<td width="15%"> 


![Checkmark]( ../../Linked_Image_Files/checkmark.png)

 </td>
<td valign="top"> 


If you prefer, you can [use the PowerShell Start-AzureRmAutomationDscCompilationJob](https://azure.microsoft.com/en-us/documentation/articles/automation-dsc-compile/#compiling-a-dsc-configuration-with-windows-powershell) to compile the configuration file. 

 </td>
</tr>
</tbody>
</table>

