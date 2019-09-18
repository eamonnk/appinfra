

*DSC configurations* are Windows PowerShell scripts that define a special type of function. You can view some syntax examples and scenarios on the <a href="https://msdn.microsoft.com/en-us/powershell/dsc/configurations#configuration-syntax" target="_blank"><span style="color: #0066cc;" color="#0066cc">Configuration syntax </span></a> page.



### DSC configuration elements
We'll provide the example configurations and then discuss the elements within them. Let's start with the following example configuration:

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


- **Configuration block**. The **Configuration** block is the outermost script block. In this case, the name of the configuration is **LabConfig**. Notice the curly brackets to define the block.
- **Node block**. There can be one or more **Node** blocks. These define the nodes (computers and VMs) that you are configuring. In this example, the node targets a computer called **WebServer**. You could also call it **localhost** and use it locally on any server.
- **Resource blocks**. There can be one or more resource blocks. This is where the configuration sets the properties for the resources. In this case, there is one resource block called **WindowsFeature**. Notice the parameters that are defined. (You can read more about resource blocks at <a href="https://docs.microsoft.com/en-us/powershell/dsc/resources/resources" target="_blank"><span style="color: #0066cc;" color="#0066cc">DSC resources</span></a>.

Here is another example:

```powershell
    Configuration MyDscConfiguration
    {
        param
        (
            [string[]]$ComputerName='localhost'
        )
    
        Node $ComputerName
        {
            WindowsFeature MyFeatureInstance
            {
                Ensure = 'Present'
                Name = 'RSAT'
            }
    
            WindowsFeature My2ndFeatureInstance
            {
                Ensure = 'Present'
                Name = 'Bitlocker'
            }
        }
    }
    
    MyDscConfiguration
```

In this example, you specify the name of the node by passing it as the *ComputerName* parameter when you compile the configuration. The name defaults to "*localhost*".

Within a Configuration block, you can do  almost anything that you normally could in a PowerShell function. You can also create the configuration in any editor, such as PowerShell ISE, and then save the file as a PowerShell script with a .ps1 file type extension.
