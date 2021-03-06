

Kubernetes pods have limited lifespan, and  are replaced whenever new versions are deployed. Settings such as the IP address change regularly, so interacting with pods by using an IP address is not advised. This is why Kubernetes services exist. To simplify the network configuration for application workloads, Kubernetes uses Services to logically group a set of pods together and provide network connectivity. 

*Kubernetes Service* is an abstraction that defines a logical set of pods, combined with a policy that describes how to access them. Where pods have a shorter lifecycle, services are usually more stable and are not affected by container updates. This means that you can safely configure applications to interact with pods through the use of services. The service redirects incoming network traffic to its internal pods. Services can offer more specific functionality, based on the service type that you specify in the Kubernetes deployment file.

If you do not specify the service type, you will get the default type, which is `ClusterIP`. This means that your services and pods will receive virtual IP addresses that are only accessible from within the cluster. Although this might be a good practice for containerized back-end applications, it might not be what you want for applications that need to be accessible from the internet. You need to determine how to configure your Kubernetes cluster to make those applications and pods accessible from the internet.

### Services
The following Service types are available:

- Cluster IP. This service creates an internal IP address for use within the AKS cluster. However, it's good for internal-only applications that support other workloads within the cluster.

<p style="text-align:center;"><img src="../Linked_Image_Files/clusterip.png" alt="A workflow graphic of internal traffic being routed over port 80 to a ClusterIP and then to three pods over port 80."></p>

- NodePort. This service creates a port mapping on the underlying node, which enables the application to be accessed directly with the node IP address and port.

<p style="text-align:center;"><img src="../Linked_Image_Files/nodeport.png" alt="A workflow graphic of incoming traffic being routed over port 31000 to three AKS nodes, which are all routed to a single NodePort, and from there to three pods over port 80."></p>

- Load Balancer. this service creates an Azure Load Balancer resource, configures an external IP address, and connects the requested pods to the load balancer backend pool. To allow customers traffic to reach the application, load balancing rules are created on the desired ports. 

<p style="text-align:center;"><img src="../Linked_Image_Files/loadbalancer.png" alt="A workflow graphic of incoming traffic being routed through a load balancer to three AKS nodes, and then to two pods on port 80."></p>

### Ingress controllers
When you create a Load Balancer–type Service, an underlying Azure Load Balancer resource is created. The load balancer is configured to distribute traffic to the pods in your service on a given port. The Load Balancer only works at layer 4. The Service is unaware of the actual applications, and can't make any additional routing considerations.

Ingress controllers work at layer 7, and can use more intelligent rules to distribute application traffic. A common use of an Ingress controller is to route HTTP traffic to different applications based on the inbound URL.

<p style="text-align:center;"><img src="../Linked_Image_Files/ingresscontroller.png" alt="A workflow graphic of incoming traffic being routed from the ingress controller to a blog service, and then being routed to four pods through port 80."></p>

There are different implementations of the `Ingress Controller` concept. One example is the `Nginx Ingress Controller`, which translates the Ingress Resource into a **nginx.conf** file. Other examples are the `ALB Ingress Controller (AWS`) and the `GCE Ingress Controllers (Google Cloud)`, which make use of cloud native resources. Using the Ingress setup within Kubernetes makes it possible to easily switch the reverse proxy implementation so that your containerized workload leverages the most out of the cloud platform on which it is running.


### Azure virtual networks
In AKS, you can deploy a cluster that uses one of the following two network models:

- Basic networking. The network resources are created and configured when the AKS cluster is deployed.
- Advanced networking. The AKS cluster is connected to existing virtual network resources and configurations.
