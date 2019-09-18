
This walkthrough shows how to deploy an AKS cluster using the Azure CLI. A multi-container application that includes a web front end and a Redis Cache instance is run in the cluster. You then see how to monitor the health of the cluster and pods that run your application

### Prerequisites

- Use the cloud shell.

- You require an Azure subscription to be able to perform these steps. If you don't have one, you can create it by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> page.

### Steps

1. Open Azure Cloud Shell by going to https://shell.azure.com, or using the Azure Portal and selecting **Bash** as the environment option.

  <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-javaappinappservice1.png" alt="Open cloud shell icon in Bash Environment selected and highlighted"></p>


2. Create an Azure resource group by running the  following command:

    ```cli
    az group create --name myResourceGroup --location < datacenter nearest you >
    ```

3. Create an AKS cluster by running the following command:

    ```bash
    az aks create \
        --resource-group myResourceGroup \
        --name myAKSCluster \
        --node-count 1 \
        --enable-addons monitoring \
        --generate-ssh-keys
    ```

After a few minutes, the command completes and returns JSON-formatted information about the cluster.

4. To manage a Kubernetes cluster, you use `kubectl`, the Kubernetes command-line client. If you use Azure Cloud Shell, `kubectl` is already installed. To install `kubectl` locally, use the following command:


    ```bash
    az aks install-cli
    ```

5. To configure `kubectl` to connect to your Kubernetes cluster, use the `az aks get-credentials` command. This command downloads credentials and configures the Kubernetes CLI to use them:

    ```bash
    az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
    ```

6. Verify the connection to your cluster by running the following command. Make sure that the status of the node is Ready:

    ```bash
    kubectl get nodes
    ```

7. Create a file named **azure-vote.yaml**, and then copy it into the following `YAML` definition. If you use the Azure Cloud Shell, you can create this file using **vi** or **nano** as if working on a virtual or physical system:

    ```YAML
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: azure-vote-back
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: azure-vote-back
      template:
        metadata:
          labels:
            app: azure-vote-back
        spec:
          containers:
          - name: azure-vote-back
            image: redis
            resources:
              requests:
                cpu: 100m
                memory: 128Mi
              limits:
                cpu: 250m
                memory: 256Mi
            ports:
            - containerPort: 6379
              name: redis
    apiVersion: v1
    kind: Service
    metadata:
      name: azure-vote-back
    spec:
      ports:
      - port: 6379
      selector:
        app: azure-vote-back
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: azure-vote-front
    spec:
      replicas: 1
      selector:
        matchLabels:
          app: azure-vote-front
      template:
        metadata:
          labels:
            app: azure-vote-front
        spec:
          containers:
          - name: azure-vote-front
            image: microsoft/azure-vote-front:v1
            resources:
              requests:
                cpu: 100m
                memory: 128Mi
              limits:
                cpu: 250m
                memory: 256Mi
            ports:
            - containerPort: 80
            env:
            - name: REDIS
              value: "azure-vote-back"
    apiVersion: v1
    kind: Service
    metadata:
      name: azure-vote-front
    spec:
      type: LoadBalancer
      ports:
      - port: 80
      selector:
        app: azure-vote-front
    ```
    
    
 8. Deploy the application by running the following command:

    ```bash
    kubectl apply -f azure-vote.yaml
    ```
    
    You should receive output showing the Deployments and Services were created successfully after it runs as per the below.
    
    ```bash
    deployment "azure-vote-back" created
    service "azure-vote-back" created
    deployment "azure-vote-front" created
    service "azure-vote-front" created
    ```


9. When the application runs, a Kubernetes service exposes the application front end to the internet. This process can take a few minutes to complete. To monitor progress run the command


    ```bash
    kubectl get service azure-vote-front --watch
    ```

10. Initially the **EXTERNAL-IP** for the azure-vote-front service is shown as pending.

    ```bash
    NAME               TYPE           CLUSTER-IP   EXTERNAL-IP   PORT(S)        AGE
    azure-vote-front   LoadBalancer   10.0.37.27   < pending >     80:30572/TCP   6s
    ```

11. When the **EXTERNAL-IP** address changes from pending to an actual public IP address, use **CTRL-C** to stop the `kubectl` watch process. The following example output shows a valid public IP address assigned to the service:


    ```bash
    azure-vote-front   LoadBalancer   10.0.37.27   52.179.23.131   80:30572/TCP   2m
    ```
    
12. To see the Azure Vote app in action, open a web browser to the external IP address of your service.

<p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-deployconfiguraksapp.png" alt="A web browser displaying the Azure Voting app."></p>


Monitor health and logs. When the AKS cluster was created, Azure Monitor for containers was enabled to capture health metrics for both the cluster nodes and pods. These health metrics are available in the Azure portal. To see current status, uptime, and resource usage for the Azure Vote pods, complete the following steps in the Azure portal:

13. Open a web browser to the Azure portal https://portal.azure.com.

14. Select your resource group, such as myResourceGroup, then select your AKS cluster, such as myAKSCluster.

15. Under Monitoring on the left-hand side, choose Insights

16. Across the top, choose to + Add Filter

17. Select Namespace as the property, then choose < All but kube-system >

18. Choose to view the Containers. The azure-vote-back and azure-vote-front containers are displayed, as shown in the following example:

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-deployconfiguraksapp2.png" alt="A web browser in the Azure Portal displaying the container properties."></p>


19. To see logs for the azure-vote-front pod, select the View container logs link on the right-hand side of the containers list. These logs include the stdout and stderr streams from the container

    <p style="text-align:center;"><img src="../Linked_Image_Files/walkthrough-deployconfiguraksapp3.png" alt="A web browser in the Azure Portal displaying the container logs."></p>

> **Note**: If you are not continuing to use the Azure resources, remember to delete them to avoid incurring costs.
