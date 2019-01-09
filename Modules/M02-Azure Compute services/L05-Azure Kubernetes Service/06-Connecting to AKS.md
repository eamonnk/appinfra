<h2><span style="color: #0000CD;">Connecting to Kubernetes</span></h2>
To deploy to an ACS cluster that has Kubernetes as the cluster orchestrator, we deploy containers by using the command-line tool `kubectl`.

You can install this command-line tool on your machine by running the following command from an elevated command prompt:
```
az acs kubernetes install-cli
```
Next, put the location where you installed it in your Windows system environment %PATH% variable.

Now we need credentials to create a secure connection to the master node. The Azure CLI will help us with that. Execute the following command to download connection information so that we can use it with the kubectl tool.

```
az acs kubernetes get-credentials -g myResourceGroup -n containerservice-myACSName 

```

The standard way of creating a Kubernetes ACS cluster uses the following command:
```
az acs create --orchestrator-type=kubernetes -g myResourceGroup -n containerservice-myACSName --windows --admin-username azureuser --admin-password myPassword12 --generate-ssh-keys
```
The option generate-ssh-keys will generare a default ssh key file pair called **id_rsa** and **id_rsa.pub** if they do not already exist. 

<h2><span style="color: #0000CD;">Deploying to Kubernetes</span></h2>
After this, you can issue a command to deploy a new service by using the command:
```
kubectl create deployment mydeploymentname --image=myrepo/myimage
```

Next, you can expose the service to the outer world for use by exposing this service to the public load balancer. This is done with the command:

```
kubectl expose deployment nameofdeployment --port=80
```

It will expose the deployment as a service on port 80. You can see which public IP you can use to access the service by using the command:

```
kubectl get service
```

This will give you a list of services and the IP address + port on which they are listening.