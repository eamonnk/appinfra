

Azure Automation runbooks are provided to help eliminate the time it takes to build custom solutions. These runbooks have already been built by Microsoft and the community and can be used with or without modification. Runbooks can be imported form the <a href="https://gallery.technet.microsoft.com/scriptcenter/site/search?f[0].Type=RootCategory&f[0].Value=WindowsAzure&f[1].Type=SubCategory&f[1].Value=WindowsAzure_automation&f[1].Text=Automation" target="_blank"><span style="color: #0066cc;" color="#0066cc">Runbook Gallery</span></a>.

> **Note**: The new Azure PowerShell **Az module** is not supported in Azure Automation. Any scripts downloaded from the PowerShell Gallery with these **Az** cmdlets will not work in Azure Automation.


### Choosing items from the Runbook Gallery
In the Azure portal, you can import directly from the Runbook Gallery by 
1. opening your Automation account and click on **Process Automation** > **Runbooks**
2. Then in the runbooks pane click on the **Browse gallery** button, 
3. The runbook gallery is displayed within the portal and you then need to locate the runbook gallery item that you want, selecting it, and click the **Import** button.
4. When clicking on the runbooks, you are able to view the code or a visualization of the code and also able to click to view the source project on <a href="https://gallery.technet.microsoft.com/scriptcenter" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://gallery.technet.microsoft.com/scriptcenter</span></a>, where you cna view detailed descriptions, ratings, Q and A and more details.

    <p style="text-align:center;"><img src="../Linked_Image_Files/runbookgallery1.png" alt="Screenshot of Star Azure V2 VMs runbook in the runbook gallery in Azure Automation with IMport and View Source Project options highlighted. Also present is a graphical visualization of the runbook."></p>

> **Note**: **Python** runbooks are also available from the <a href="https://gallery.technet.microsoft.com/scriptcenter" target="_blank"><span style="color: #0066cc;" color="#0066cc">script center gallery</span></a>. You just need to filter by language and select **Python**

> **Note**: Also, you cannot import directly from the Runbook Gallery by using Windows PowerShell.   