<h1><strong><span style="color: #0000CD;">Source Control Integration</span></strong></h1> 

Azure Automation supports source control integration so that you can associate runbooks in your Automation account to a GitHub source control repository. Source control allows you to easily collaborate with your team, track changes, and roll back to earlier versions of your runbooks. For example, source control allows you to sync different branches in source control to your development, test, or production Automation accounts, making it easy to promote code that has been tested in your development environment to your production Automation account.

Source control allows you to push code from Azure Automation to source control or pull your runbooks from source control to Azure Automation.


<table border="0" cellpadding="0">
<tbody>
<tr>
<td width="15%"> 


![Checkmark]( ../../Linked_Image_Files/checkmark.png)

 </td>
<td valign="top"> 


Source control supports pulling and pushing Windows PowerShell workflow runbooks and PowerShell runbooks. Graphical runbooks are not yet supported.  

 </td>
</tr>
</tbody>
</table>


After [creating a repository in GitHub](https://help.github.com/articles/create-a-repo/), you need only click **Set Up Source Control** from the Automation Account blade in the Azure portal. When the blade opens, you can configure your GitHub account details. The parameters will be displayed on the Set Up Source Control blade.

![Screenshot of the Set Up Source Control blade, with the Choose source: GitHub option selected.]( ../../Linked_Image_Files/1.5.6.png)
