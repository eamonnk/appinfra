

Kubernetes uses the term pod to package applications. A *pod* is a deployment unit, and it represents a running process on the cluster. It consists of one or more containers, and configuration, storage resources, and networking support. Pods are usually created by a controller, which monitors it and provides self-healing capabilities at the cluster level. 

Pods are described by using YAML or JSON. Pods that work together to provide functionality are grouped into services to create *microservices*. For example, a front-end pod and a back-end pod could be grouped into one service.

Deploying an application to Kubernetes can be done by using the `kubectl` CLI, which can manage the cluster. By running `kubectl` on your build agent, it's possible to deploy Kubernetes pods from Azure DevOps. It's also possible to use the management API directly. There is also a specific Kubernetes task called Deploy To Kubernetes that is available in Azure DevOps. More information about this will be covered in the demonstration.

#### Continuous delivery

To achieve continuous delivery, the build-and-release pipelines are run for every check-in on the Source repository.
