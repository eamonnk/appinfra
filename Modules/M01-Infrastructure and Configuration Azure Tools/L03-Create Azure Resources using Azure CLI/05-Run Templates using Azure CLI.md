
We have added the custom script extension to a sample deployment json template. You can view the sample azure deploy template with the custom script extension resource included [here](https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json). 

In the following steps we will deploy the template and verify the result using **Azure CLI**.

1. Create a resource group to deploy your resources to, by running the below command

```azurecli
az group create --name <resource group name> --location  <your nearest datacenter>
```

2. From Cloud Shell, run `curl` to download the template you used previously from GitHub.

    ```bash
    curl https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json > C:\temp\azuredeploy.json
    ```

3. Validate the template by running the below command, substituting the values with your own, 

 
```azurecli
az group deployment validate \
  --resource-group <rgn>[sandbox resource group name]</rgn> \
  --template-file C:\temp\azuredeploy.json \
  --parameters adminUsername=$USERNAME \
  --parameters adminPassword=$PASSWORD \
  --parameters dnsLabelPrefix=$DNS_LABEL_PREFIX
```
4. Deploy the resource by running the below command, substituting the same values as earlier.

```azurecli
az group deployment create \
  --name MyDeployment \
  --resource-group <rgn>[sandbox resource group name]</rgn> \
  --template-file azuredeploy.json \
  --parameters adminUsername=$USERNAME \
  --parameters adminPassword=$PASSWORD \
  --parameters dnsLabelPrefix=$DNS_LABEL_PREFIX
```

5. Obtain the IP address by running the command

```azurecli
    IPADDRESS=$(az vm show \
      --name SimpleWinVM \
      --resource-group <rgn>[sandbox resource group name]</rgn> \
      --show-details \
      --query [publicIps] \
      --output tsv)
```
6. Run `curl` to access your web server and verify the successful deployment and running of the custom script extension.

    ```bash
    curl $IPADDRESS
    ```

    You see this.

    ```html
    <html><body><h2>Welcome to Azure! My name is SimpleWinVM.</h2></body></html>
    ```
> **Note**: Don't forget to delete any resources you deployed to avoid incurring additional costs on them.