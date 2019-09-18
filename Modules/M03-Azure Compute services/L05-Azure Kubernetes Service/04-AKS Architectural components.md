A Kubernetes cluster is divided into two components:

- Cluster master nodes, which provide the core Kubernetes services and orchestration of application workloads.
- Nodes that run your application workloads.


<p style="text-align:center;"><img src="../Linked_Image_Files/akscomponents1.png" alt="Graphic representing an Azure-managed cluster master, which is in a box. A second box within contains a scheduler, controller, API server, and storage. A separate customer-managed node box has boxes within containing container runtime, container, kubelet and kube-proxy. Kubelet container and the Node box have arrows pointing to scheduler in the Cluster master box. "></p>

### Cluster master
When you create an AKS cluster, a cluster master is automatically created and configured. This cluster master is provided as a managed Azure resource abstracted from the user. There is no cost for the cluster master, only the nodes that are part of the AKS cluster.

The cluster master includes the following core Kubernetes components:
- kube-apiserver. The API server is how the underlying Kubernetes APIs are exposed. This component provides the interaction for management tools such as kubectl or the Kubernetes dashboard.
- etcd. To maintain the state of your Kubernetes cluster and configuration, the highly available etcd is a key value store within Kubernetes.
- kube-scheduler. When you create or scale applications, the Scheduler determines what nodes can run the workload, and starts them.
- kube-controller-manager. The Controller Manager oversees a number of smaller controllers that perform actions such as replicating pods and managing node operations.


### Nodes and node pools
To run your applications and supporting services, you need a Kubernetes node. An *AKS cluster*, which is an Azure virtual machine (VM) that runs the Kubernetes node components and container runtime, contains one or more nodes:

- The *kubelet* is the Kubernetes agent that processes the orchestration requests from the cluster master, and scheduling of running the requested containers.
- Virtual networking is handled by the kube-proxy on each node. The proxy routes network traffic and manages IP addressing for services and pods.
- The *container runtime* is the component that allows containerized applications to run and interact with additional resources such as the virtual network and storage. In AKS, Docker is used as the container runtime.

Nodes of the same configuration are grouped together into *node pools*. A Kubernetes cluster contains one or more node pools. The initial number of nodes and size are defined when you create an AKS cluster, which creates a default node pool. This default node pool in AKS contains the underlying VMs that run your agent nodes.

### Pods
Kubernetes uses pods to run an instance of your application. A pod represents a single instance of your application. Pods typically have a 1:1 mapping with a container, although there are advanced scenarios where a pod might contain multiple containers. These multi-container pods are scheduled together on the same node, and allow containers to share related resources.

When you create a pod, you can define resource limits to request a certain amount of CPU or memory resources. The Kubernetes Scheduler attempts to schedule the pods to run on a node with available resources to meet the request. You can also specify maximum resource limits that prevent a given pod from consuming too much compute resource from the underlying node. 

> **Note**: A best practice is to include resource limits for all pods to help the Kubernetes Scheduler understand what resources are needed and permitted.

A pod is a logical resource, but the container (or containers) is where the application workloads run. Pods are typically ephemeral, disposable resources. Therefore, individually scheduled pods miss some of the high availability and redundancy features Kubernetes provides. Instead, pods are usually deployed and managed by Kubernetes controllers, such as the Deployment controller.
