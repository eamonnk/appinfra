There is a [sample deployment template](https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json) written in JSON, which contains a Custom Script Extension, available from GitHub. The following steps show how to deploy the template, and verify the result using the Azure CLI.

:one: . Create a Resource Group to deploy your resources to, by running the following command.

  ```azurecli
    az group create --name <resource group name> --location  <your nearest datacenter>
  ```

:two: . From the Azure Cloud Shell, run `curl`, to download the template from GitHub.

  ```bash
    curl https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json > C:\temp\azuredeploy.json
  ```

:three: . Validate the template by running the following command, you should substitute the values with your own.

  ```azurecli
    az group deployment validate \
      --resource-group <rgn>[sandbox resource group name]</rgn> \
      --template-file C:\temp\azuredeploy.json \
      --parameters adminUsername=$USERNAME \
      --parameters adminPassword=$PASSWORD \
      --parameters dnsLabelPrefix=$DNS_LABEL_PREFIX
  ```

:four: . Deploy the resource by running the following command, substituting the same values as you did in the previous step.

  ```azurecli
    az group deployment create \
      --name MyDeployment \
      --resource-group <rgn>[sandbox resource group name]</rgn> \
      --template-file azuredeploy.json \
      --parameters adminUsername=$USERNAME \
      --parameters adminPassword=$PASSWORD \
      --parameters dnsLabelPrefix=$DNS_LABEL_PREFIX
  ```

:five: . Obtain the IP address by running the following command.

  ```azurecli
    IPADDRESS=$(az vm show \
      --name SimpleWinVM \
      --resource-group <rgn>[sandbox resource group name]</rgn> \
      --show-details \
      --query [publicIps] \
      --output tsv)
  ```
:six: . Run `curl` to access your web server, and to verify that the deployment and Custom Script Extension ran successfully.

  ```bash
    curl $IPADDRESS
  ```
:seven: . A welcome message similar to the following should now be displayed.

  ```html
      <html><body><h2>Welcome to Azure! My name is SimpleWinVM.</h2></body></html>
  ```
> :information_source: Remember to delete any resources you deployed to avoid incurring additional costs.
