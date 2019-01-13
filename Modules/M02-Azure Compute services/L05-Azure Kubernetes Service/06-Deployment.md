Kubernetes uses the term *pod* to refer to package applications. A pod is a deployment unit, and it represents a running process on the cluster. It consists of one or more containers, and configuration, storage resources, and networking support. Pods are usually created by a controller, which monitors it and provides self-healing capabilities at the cluster level.

Pods are described by using *YAML* or *JSON*. Pods that work together to provide functionality are grouped into services to create *microservices*. For instance, a front-end pod and a back-end pod could be grouped into one service.

Deploying an application to Kubernetes can be done by using the `kubectl` Command Line Interface (CLI), which can manage the cluster. By running `kubectl` on your build agent, you can deploy Kubernetes pods from Azure DevOps. It's also possible to use the management API directly.

> :information_source: For information about the `kubectl` CLI read the section of the Kubernetes reference documentation called [Overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/).

There is a specific Kubernetes task called *Deploy To Kubernetes* [available in Azure DevOps](https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/kubernetes?view=vsts), which you will learn more about this in the next lesson.

#### Continuous delivery

To achieve continuous delivery, the build-and-release pipelines are run for every check-in on the source repository.
