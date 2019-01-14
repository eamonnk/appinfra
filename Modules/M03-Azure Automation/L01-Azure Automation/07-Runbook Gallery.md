Using runbooks from the Azure Automation [Runbook Gallery](https://gallery.technet.microsoft.com/scriptcenter/site/search?f[0].Type=RootCategory&f[0].Value=WindowsAzure&f[1].Type=SubCategory&f[1].Value=WindowsAzure_automation&f[1].Text=Automation) can reduce the time it takes to build your own custom solutions. Runbooks within the Runbook Gallery have been pre-built by Microsoft and the development community. You can import runbooks from the Runbook Gallery and use them with or without modification.

> :information_source: The new Azure PowerShell `Az module` is not supported by Azure Automation. Any scripts downloaded from the Runbook Gallery with `Az cmdlets` will not work in Azure Automation.

### Choosing items from the Runbook Gallery

The following describes how to import items from the Runbook Gallery in Azure portal.

1. Open your Automation Account and choose **Process Automation** > **Runbooks**
2. In the **Runbooks** pane, select the **Browse gallery** button.
3. Locate the Runbook Gallery item you want, select it, and choose the **Import** button.
4. When you select a runbook from the Runbook Gallery, you can view the code or a visualization of the code. It is also possible to view the source code on [Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter). Microsoft Script Center provides access to detailed descriptions, ratings, questions and answers, as well as additional details.

<p style="text-align:center;"><img src="../Linked_Image_Files/runbookgallery1.png" alt="Screenshot of the Star Azure V2 VMs runbook in the Azure Automation Runbook Gallery. Witihin the image, 'IMport' and 'View Source Project' options are highlighted. A graphical visualization of the runbook is also shown."></p>

> :information_source: Python runbooks are also available from the [Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter). To view Python runbooks, you need to set the filter option to 'filter by language' and then select 'Python'.
>
> Be advised that you cannot import directly from the Runbook Gallery using Windows PowerShell.   
