<h1><strong><span style="color: #0000CD;">Kubernetes Networking</span></strong></h1>

When using Kubernetes as cluster management product, you will encounter some Kubernetes-specific concepts such as *pods, services*, and *deployments*. Another concept within Kubernetes is *ingress*. In this lesson, we'll talk about what ingress is and how it helps to configure a reverse proxy within your Kubernetes cluster. But before we do that, we will briefly look at the other Kubernetes concepts.

<h2><span style="color: #0000CD;">Pods and services</span></h2>

Deployment of resources into a Kubernetes cluster works based on a Kubernetes deployment file (in YAML format). Within this deployment file, you specify the resources that you want to deploy to a cluster. For each resource that must be deployed, you specify a section marked by three hyphens. Within each section, you specify the type of resource to be deployed.

### Pods
A Kubernetes pod is a group of one or more containers that need to run in a shared context (storage/network), co-located and co-scheduled on the same node within the Kubernetes cluster. Let’s say that you have an application that consists of two parts: a web API and a local cache that are most effective when running on the same node. In this case, you would define a pod with two container images. 

A pod is the implicitly defined logical unit of container instance management within Kubernetes. Every container instance created in a pod will request an IP address from the DHCP server in the local cluster network. Additionally, each pod will get an internal DNS record based on the deployment name. Pods deployed as part of the Kubernetes platform act as DHCP and DNS server. Pods become accessible from anywhere in the cluster, based on their DNS name and exposed ports. 

### Services
Kubernetes pods have limited lifespan, and they are replaced whenever new versions are deployed. Settings such as the IP address change regularly, so interacting with pods by using an IP address is not advised. This is why Kubernetes services exist. 

A Kubernetes service is an abstraction that defines a logical set of pods, combined with a policy that describes how to access them. Where pods have a shorter lifecycle, services are usually more stable, and are not affected by container updates. This means that you can safely configure applications to interact with pods through the use of services. The service redirects incoming network traffic to its internal pods. Services can offer more specific functionality, based on the service type that you specify in the Kubernetes deployment file.

If you do not specify the service type, you will get the default type: `ClusterIP`. This means that your services and pods will receive virtual IP addresses that are only accessible from within the cluster. Although this might be a good practice for containerized back-end applications, it might not be what you want for applications that need to be accessible from the internet. You need to determine how to configure your Kubernetes cluster to make those applications/pods accessible from the internet.

### Reverse proxy implementations

**1. Load balancer service**

One way of exposing containerized applications to the outside world, is by creating a service of type `LoadBalancer`. 

For each LoadBalancer service created within the cluster, Kubernetes will configure a public IP address. When deploying a small set of services, this solution is a good option. However, if you have dozens of applications, using this approach means that you will have to manage the mapping of those IP addresses on DNS records. Also, if you are running your Kubernetes cluster in Azure, you will reach the (soft) limit of 20 public IP addresses allowed per Azure subscription.

**2. Reverse Proxy**

Another way of making your applications accessible from the internet is by using reverse proxy technology such as Nginx. In this setup, you register a Kubernetes service of type `LoadBalancer` to configure a single public IP address for your Kubernetes cluster, and configure it to route all traffic to a pod that performs the role of reverse proxy. The pod is responsible for routing network traffic to internal services of type `ClusterIP`. 

This approach resolves the public IP address issue, but it also has a disadvantage. The configuration of the reverse proxy requires constant maintenance as services are renamed, added, and removed.  

**3. Ingress**

Instead of having a technology-specific reverse proxy configuration, Ingress offers a built-in solution to define the proxy configuration in a technology-independent format. It uses the same syntax that other Kubernetes resources use. The configuration file is called the `Ingress Resource`. It is consumed by an `Ingress Controller`, which is able to translate the content of the Ingress Resource in a technology-specific definition.

There are different implementations of the `Ingress Controller` concept. One example is the `Nginx Ingress Controller`, which translates the Ingress Resource into a **nginx.conf** file. Other examples are the `ALB Ingress Controller (AWS`) and the `GCE Ingress Controllers (Google Cloud)` that make use of cloud native resources. Using the Ingress setup within Kubernetes makes it possible to easily switch the reverse proxy implementation so that your containerized workload leverages the most out of the cloud platform on which you are running.