
# Demo Walk-Through: Interacting with K8s Clusters Using Kubectl, Web UI, and Web API #

## Prepare

1. Open putty.exe, load "k8s".

2. Open 3 browser tabs:

"http://localhost:8001/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard/#/pod?namespace=default" 

"http://localhost:8080/api/v1/namespaces/default/pods" 

"http://localhost:8080/api/v1/namespaces/default/pods/iis-3755450956-wgtw2"

## Intro

In this demo, we will review some options to interact with an existing Kubernetes cluster.

We will show you how to view information about running applications, or pods, by using the command line tool `kubectl` (say: 'kubecontrol'), by using the Web UI and the Management API that come with Kubernetes. The Web UI and kubectl both use the Web API under the hood.

## Slide 1

### Using PuTTY to set up the connection
PuTTY is a free implementation of SSH and Telnet for Windows and Unix platforms. Later I will connect to the Master node using putty.

- To do this, I’ve configured a connection to be opened to the master node's DNS name, at port 22.

- Also, by configuring port forwarding rules, I can use the browser on my laptop to manage the cluster.

**Show putty / auth / tunnel**

The Kubernetes Web UI is at port 8001, and the management API is hosted at port 8080. I have mapped these ports from the master node in Azure, to my local machine.

## Slide 2

### Kubectl CLI

Kubectl is a command-line tool that you can use to manage your Kubernetes cluster.

**Show Putty connect**

To create an SSH connection to the master node, I'll click 'open' in Putty. Next, I'll provide the username of the administrator, and a passphrase.
**Type u:msftdevopscourse p:Msftcourse01!**

Next I’ll type `kubectl get pods`, this will display information about deployed workloads that are currently running. 
If I want to filter the list to display information about a single pod, I can use the command `kubectl get pod` followed by its name. **highlight and copy name**

**Type: `kubectl get pod {paste name}`**

### Web UI
The same pods can be listed by using the Web UI. The web UI must be explicitly started. To do that, I execute `kubectl proxy`. Once the web UI is running, I can use my browser to access it.

**Type: `kubectl proxy`**

**Show browser**

By navigating to the URL "http://localhost:8001/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard/#/pod?namespace=default" 

I can see the same pods as we saw earlier. By clicking on one of the Pods, I can see more detailed information about it.

By navigating to the URL
"http://localhost:8080/api/v1/namespaces/default/pods" I am accessing the Management API directly, to again see the same information about the pods. 

**Now navigate to this URL:**
"http://localhost:8080/api/v1/namespaces/default/pods/iis-3755450956-wgtw2"
By appending the name of an existing pod, I can see its details.




