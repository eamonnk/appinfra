# Demo Walk-Through - Docker Compose Deployment to a Service Fabric Cluster

Docker Compose is a way to deploy containers to a cluster, by means of a declaration of desired state.
It uses a YAML file to describe which containers need to be deployed.

### YAML definition
A sample of a YAML definition would be similar to this:

``` yaml
version: '3'

services:

  web:
    image: microsoft/iis:nanoserver
    ports:
      - "80:80"

networks:
  default:
    external:
      name: nat
```

This sample file would result in a single container based on the image named `microsoft/iis:nanoserver`. We did not specify a container registry to use, so Docker Hub is used by default. The container exposes Internet Information Services at port 80. We connect the container port to the host port 80, by specifying `80:80`. Finally, we selected the default `nat` network to connect containers.

In the next paragraph, we will deploy a Docker Compose file.

### Deploying a Docker Compose file

1. Connect to the existing cluster by using the PowerShell command `Connect-ServiceFabricCluster`:

    ```powershell
    `Connect-ServiceFabricCluster -ConnectionEndpoint devopsdemowin.westeurope.cloudapp.azure.com:19000 -FindType FindByThumbprint -FindValue B00B6FF39F5A50702AF3493B2C13237E80DE6734 -StoreName My -StoreLocation CurrentUser -X509Credential -ServerCertThumbprint B00B6FF39F5A50702AF3493B2C13237E80DE6734`
    ```

    > **Note**: The values for this command will be different for your own cluster.

2. Deploy the docker-compose.yml file by using the following command: 

    ```powershell
    `New-ServiceFabricComposeDeployment -DeploymentName ComposeDemo -Compose x:\docker-compose.yml`
    ```

3. You can check the deployment status by using this command:

    ```powershell
    `Get-ServiceFabricComposeDeploymentStatus -DeploymentName ComposeDemo`
    ```

4. When the deployment has completed, you can navigate to your new service by opening a browser and navigating to the Service Fabric cluster domain name at port 80.
  For example: `http://devopsdemowin.westeurope.cloudapp.azure.com`
  You should see the information page of IIS running as a container on your Service Fabric cluster.


5. To remove a deployment, run:

    ```powershell
    Remove-ServiceFabricComposeDeployment -DeploymentName ComposeDemo
    ```