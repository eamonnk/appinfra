DSC configurations are Windows PowerShell scripts that define a special type of function.

:information_source: For examples of DSC configurations, syntax, and use case scenarios, see the page [simple configurations](https://msdn.microsoft.com/en-us/powershell/dsc/configurations#configuration-syntax)

### DSC configuration elements

The following is an example configuration.

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

- *Configuration block*. is the outermost script block. In the example configuration, the name of the configuration is `LabConfig`. Notice how braces are used to define the block.

- *Node block*. There can be one or more node blocks. These define the nodes (computers and VMs) that you are configuring. In the example configuration, the node targets a computer called `*WebServer`. You could also call it `localhost` and use it locally on a server.

- *Resource blocks*. There can be one or more [resource blocks](https://docs.microsoft.com/en-us/powershell/dsc/resources/resources). This is where the configuration sets the properties for the resources. In the example configuration, there is one resource block called `WindowsFeature`. Notice the parameters that are defined.

The following is another example configuration.

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

In the second example configuration, you specify the name of the node by passing it as the `ComputerName` parameter when you compile the configuration. The name defaults to `localhost`.

Within a Configuration block, you can do anything that you normally could in a PowerShell function.

You can create the configuration in any editor. For example, using the PowerShell ISE, save the file as a PowerShell script with a `ps1` file type extension.
