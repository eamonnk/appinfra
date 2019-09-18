
Azure Automation runbooks are provided to help eliminate the time it takes to build custom solutions. These runbooks have already been built by Microsoft and the Microsoft community, and can be used with or without modification. You can import runbooks from the <a href="https://gallery.technet.microsoft.com/scriptcenter/site/search?f[0].Type=RootCategory&f[0].Value=WindowsAzure&f[1].Type=SubCategory&f[1].Value=WindowsAzure_automation&f[1].Text=Automation" target="_blank"><span style="color: #0066cc;" color="#0066cc">Runbook Gallery</span></a>.

> **Note**: The new Azure PowerShell **Az module** is not supported in Azure Automation. Any scripts downloaded from the PowerShell Gallery with these **Az** cmdlets will not work in Azure Automation.


### Choosing items from the Runbook Gallery
In the Azure portal, you can import directly from the Runbook Gallery using the following steps:

1. Open your Automation account and select **Process Automation** > **Runbooks**.
2. In the runbooks pane, select **Browse gallery**.
3. From the runbook gallery, locate the runbook gallery item that you want, select it, and then select **Import**.

When browsing through the runbooks in the script center library, you can view the code or a visualization of the code. You also can view the source project along with a detailed description, ratings, questions and answers, and more. for more information, refer to <a href="https://gallery.technet.microsoft.com/scriptcenter" target="_blank"><span style="color: #0066cc;" color="#0066cc">Script resources for IT professionals</span></a>.

<p style="text-align:center;"><img src="../Linked_Image_Files/runbookgallery1.png" alt="Screenshot of Star Azure V2 VMs runbook in the runbook gallery in Azure Automation. Both the Import and View Source Project options are highlighted. A graphical visualization of the runbook also displays."></p>

> **Note**: Python runbooks are also available from the script center gallery. To find them, filter by language and select **Python**.

> **Note**: You cannot use PowerShell to import directly from the Runbook Gallery.
