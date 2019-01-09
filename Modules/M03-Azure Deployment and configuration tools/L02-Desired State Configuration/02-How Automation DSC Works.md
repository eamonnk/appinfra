

![This screenshot is made up of three sections. Section 1 is Configurations. Section 2 is Node Configurations, and Section 3 is Nodes. On the left, 1: Configurations has a code window with text beneath that says “1 or more per automation account.” An arrow labeled “Compiled, put on pull server (via compilation jobs)” points from section one to section 2. In the middle, 2: Node Configurations (.MOF configuration documents) has three Sharepoint.WebService icons. Text below the icons says “1 or more per Configuration.” An arrow labeled “Applied (via node pulls)” points from section 2 to section 3. On the right, 3: Nodes has six Node icons, with the text “1 or more per Node Configuration.”]( ../../Linked_Image_Files/2.2.1.png)

1.  Create a Windows PowerShell script with the configuration element.
2.  Upload the script to Azure Automation and compile the script into a [Managed Object Format (MOF) file](https://msdn.microsoft.com/en-us/library/aa823192(v=vs.85).aspx). The file is transferred to the DSC pull server.
3.  Define the nodes that will use the configuration.



<table border="0" cellpadding="0">
<tbody>
<tr>
<td width="15%"> 


![Checkmark]( ../../Linked_Image_Files/checkmark.png)

 </td>
<td valign="top"> 


The next lesson discusses each step in greater detail. 

 </td>
</tr>
</tbody>
</table>

