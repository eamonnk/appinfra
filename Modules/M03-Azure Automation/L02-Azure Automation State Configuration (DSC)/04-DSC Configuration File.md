

DSC configurations are Windows PowerShell scripts that define a special type of function. You can view some syntax examples and scenarios in some <a href="https://msdn.microsoft.com/en-us/powershell/dsc/configurations#configuration-syntax" target="_blank"><span style="color: #0066cc;" color="#0066cc">simple configurations</span></a> page.



### DSC configuration elements
We'll provide some example configurations and then discuss the elements within them.

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


- *Configuration block* - The **Configuration** block is the outermost script block. In this case, the name of the configuration is **LabConfig.** Notice the curly brackets to define the block.

- *Node block*  - There can be one or more **Node** blocks. These define the nodes (computers and VMs) that you are configuring. In this example, the node targets a computer called **WebServer**. You could also call it **localhost** and us it locally on any server.

- *Resource blocks* - Lastly, there can be one or more <a href="https://docs.microsoft.com/en-us/powershell/dsc/resources/resources" target="_blank"><span style="color: #0066cc;" color="#0066cc">resource blocks</span></a>. This is where the configuration sets the properties for the resources. In this case, there is one resource block called **WindowsFeature.** Notice the parameters that are defined.

Another example is listed below

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

In the above example, you specify the name of the node by passing it as the ComputerName parameter when you compile the configuration. The name defaults to "localhost".

Within a Configuration block, you can do anything that you normally could in a PowerShell function.

You can create the configuration in any editor, such as the PowerShell ISE. Save the file as a PowerShell script with a ps1 file type.
