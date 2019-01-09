<h1><strong><span style="color: #0000CD;">Introduction to AKS</span></strong></h1>

In October 2017, Microsoft introduced AKS, a managed Kubernetes offering in Azure. This offering manages much of the Kubernetes resources for the end user. With an easy command or by using a template, you can create a cluster of managed virtual machines ready to run containerized applications. Azure AKS manages the following aspects of a Kubernetes cluster for you:

* Provide Kubernetes version upgrades and patching.
* Performs simple cluster scaling.
* Enables master nodes to be fully managed by Microsoft.
* Allows paying only for running agent nodes. The master nodes are free.

At this writing, AKS is in public preview. It is available for testing in a subset of Azure regions (East US, West Europe, Central US, Canada Central, and Canada East). When AKS becomes generally available, it will be the successor of Azure Container Service. So instead of having to manage your Azure cluster resources yourself, Microsoft can manage much of the work. 

<h2><span style="color: #0000CD;">Deploying AKS</span></h2>

Deploying AKS is easy, and t can be done through the Azure CLI, the Azure Resource Manager, or the Azure Portal. For example, to create an AKS cluster by using the Azure CLI, you first create a resource group:

`az group create -n aks-training-rg -l westeurope`. 

Next, you create the AKS cluster by using:

`az aks create -g aks-training-rg -n aks-training --node-count 1 --generate-ssh-keys`. 

After using this command, two resource groups are created in your Azure subscription. One resource group is for the agent nodes resources, such as virtual machines, network interfaces, and virtual networks. The other resource group holds the meta AKS resource.

<h2><span style="color: #0000CD;">Upgrading AKS</span></h2>

The Azure CLI also helps with cluster upgrading and patching. You can easily get the available Kubernetes versions for your existing cluster by running:

`az aks get-versions -g aks-training-rg -n aks-training -o table` 

The output would look like similar to the output below:

![AKS versions display in a Command Prompt window with the following columns: Name, Resource Group, Master Version, Master Upgrades, Node Pool Version and Node Pool Upgrades.](../../Linked_Image_Files\2.2.6.aks-versions.png)

You can then upgrade the AKS cluster to one of the available versions by using:

`az aks upgrade -g aks-training-rg -n aks-training --kubernetes-version 1.8.6` 

When this operation completes, the AKS cluster is upgraded to the specified Kubernetes version. 

**Note:** At this time, downgrading is not supported.


