In the following steps we will create a virtual machine scale set, deploy a sample application, configure traffic access with a load balancer, 


### Prerequisites
- You require an Azure subscription to perform the following steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

> **Note**: If you use your own values for the parameters used in the commands below for resource group name, scale set name etc remember to change them in the subsequent commands as well, to ensure the commands run successfully.

### Steps

1. Create a Scale Set - Before you can create a scale set, create a resource group as below:
    
    ```bash
    az group create --name myResourceGroup --location < your closest datacenter > 
    ```
    
    Now create a virtual machine scale set with the below command.
    
    ```bash
    az vmss create \
      --resource-group myResourceGroup \
      --name myScaleSet \
      --image UbuntuLTS \
      --upgrade-policy-mode automatic \
      --admin-username azureuser \
      --generate-ssh-keys
    ```
    This creates a scale set named *myScaleSet* that is set to automatically update as changes are applied, and generates SSH keys if they do not exist in *~/.ssh/id_rsa.*
    
2. Deploy a sample application - To test your scale set, install a basic web application, a basic NGINX web server. The Azure Custom Script Extension is used to download and run a script that installs the sample web application on the VM instances.

    ```bash
    az vmss extension set \
      --publisher Microsoft.Azure.Extensions \
      --version 2.0 \
      --name CustomScript \
      --resource-group myResourceGroup \
      --vmss-name myScaleSet \
      --settings '{"fileUris":["https://raw.githubusercontent.com/Microsoft/PartsUnlimitedMRP/master/Labfiles/AZ-400T05-ImplemntgAppInfra/Labfiles/automate_nginx.sh"],"commandToExecute":"./automate_nginx.sh"}'
    ```

3. Allow traffic to application - When the scale set was created, an Azure load balancer was automatically deployed. The load balancer distributes traffic to the VM instances in the scale set. To allow traffic to reach the sample web application, create a load balancer rule with
    
    ```bash
    az network lb rule create \
      --resource-group myResourceGroup \
      --name myLoadBalancerRuleWeb \
      --lb-name myScaleSetLB \
      --backend-pool-name myScaleSetLBBEPool \
      --backend-port 80 \
      --frontend-ip-name loadBalancerFrontEnd \
      --frontend-port 80 \
      --protocol tcp
    ```

4. Obtain the public IP Address - To test your scale set and see your scale set in action, access the sample web application in a web browser and then obtain the public IP address of your load balancer using the command below:
    
    ```bash
    az network public-ip show \
      --resource-group myResourceGroup \
      --name myScaleSetLBPublicIP \
      --query '[ipAddress]' \
      --output tsv
    ```

5. Test your scale set - Enter the public IP address of the load balancer in to a web browser. The load balancer distributes traffic to one of your VM instances, as shown in the screenshot below:

    <p style="text-align:center;"><img src="../Linked_Image_Files/vmsswalkthrough4.png" alt="Screenshot of a web browser accessing the sample application hosted on a vm scale set via a load balancer."></p>

6. Remove the resource group, scale set, and all related resources as follows. The `--no-wait` parameter returns control to the prompt without waiting for the operation to complete. The `--yes` parameter confirms that you wish to delete the resources without an additional prompt to do so.

    ```bash
    az group delete --name myResourceGroup --yes --no-wait
    ```

