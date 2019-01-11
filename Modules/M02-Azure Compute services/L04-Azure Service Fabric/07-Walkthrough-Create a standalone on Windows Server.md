


Creating a standalone Azure Service Fabric cluster requires you to provision the hardware resources up front. After you have created and configured the required machines, you can use PowerShell to create a cluster. The required scripts and binaries can be downloaded in a single package, the Service Fabric standalone package.

![Virtual machines have an arrow labeled PowerShell pointing to Service Fabric Cluster.](../../Linked_Image_Files\3.1.2_Standalone_Cluster.png)

> **Note**: Detailed steps on how to set up a service fabric cluster ar available on the <a href="https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-creation-for-windows-server" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create a standalone cluster running on Windows Server</span> page.</a>


> **Note**: You also need to download setup files, powershell scripts for the Serve Fabric standalone package, which you run to setup a service fabric cluster. These can be downloaded from the <a href="https://go.microsoft.com/fwlink/?LinkId=730690" target="_blank"><span style="color: #0066cc;" color="#0066cc">Download Link - Service Fabric Standalone Package - Windows Server</span> page.</a> 


> **Note**: A reminder that currently standalone clusters aren't supported for Linux. Linux is supported on one-box for development and Azure Linux multi-machine clusters. As such there is no equivalent download package for Linux.

#### Process and Steps

The following steps broadly apply to all deployments, however the steps belwo are completed in the context of a standalone deployment on Windows Server. 

1. **Prepare**

    - You need to plan the required amount of server resources. Those servers need to meet the minimum requirements for Service Fabric.

    - Fault domains and upgrade domains need to be defined. 

    - The software prerequisites need to be installed. 

    - Ensure you have downloaded the Serve Fabric standalone package, which contains scripts and details needed to setup a service fabric cluster. The packaged can be downloaded from the <a href="https://go.microsoft.com/fwlink/?LinkId=730690" target="_blank"><span style="color: #0066cc;" color="#0066cc">Download Link - Service Fabric Standalone Package - Windows Server</span> page.</a> 

    - Familiarize yourself with the downloaded files. 

    - Several sample cluster configuration files are installed with the setup package you downloaded. `ClusterConfig.Unsecure.DevCluster.json` is the simplest cluster configuration: an unsecure, three-node cluster running on a single computer.

2. **Validate**

    - A validation script `TestConfiguration.ps1` is provided as part of the package. It has a Best practices analyzer that can validate some of the criteria on your resources. You can validate the environment before creating the cluster by running the command

    ```powershell
    .\TestConfiguration.ps1 -ClusterConfigFilePath .\ClusterConfig.Unsecure.DevCluster.json
    ```

3. **Create**

    - A creation script `CreateServiceFabricCluster.ps1` is also provided. Running this will create the entire cluster for you on all designated machines. You can run the command

    ```powershell
    .\CreateServiceFabricCluster.ps1 -ClusterConfigFilePath .\ClusterConfig.json -AcceptEULA
    
    ```


4. **Connect and Visualize**

    - Connect to the cluster to verify the cluster is running and available using the command
    - 
    ```powershell
    Connect-ServiceFabricCluster -ConnectionEndpoint <*IPAddressofaMachine*>:<Client connection end point port>
    ```
    i.e.
    ```powershell
    Connect-ServiceFabricCluster -ConnectionEndpoint 192.13.123.2345:19000
    ```
    - Service Fabric Explorer is a service that runs in the cluster, which you access using a browser by opening a browser and going to the location http://localhost:19000/explorer 
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/sfx.png" alt="A browser connecting to the Service Fabric dashboard"></p>

5. **Upgrade**

    - You can run the PowerShell script `Start-ServiceFabricClusterUpgrade` that is installed on the nodes as part of the deployment of the cluster to upgrade the cluster software to a specific version. 

6. **Remove**

    - If you need to remove a cluster, run the script `RemoveServiceFabricCluster.ps1`. This removes Service Fabric from each machine in the configuration

    ```powershell
    # Removes Service Fabric from each machine in the configuration
    .\RemoveServiceFabricCluster.ps1 -ClusterConfigFilePath .\ClusterConfig.json -Force
    ```


    - To removes Service Fabric from the current machine use the script and command `.\CleanFabric.ps1`. You cna ru the command

    ```powershell
    # Removes Service Fabric from the current machine
    .\CleanFabric.ps1
    ```


You'll likely add your own public IP address and load balancer to this cluster, if you need to run services that are reachable over the internet.
