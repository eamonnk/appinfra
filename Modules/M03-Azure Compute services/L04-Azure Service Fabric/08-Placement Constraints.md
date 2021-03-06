

You can use Placement constraints to:

- Isolate workloads from each other.
- Lift and shift an existing N-tier application into Azure Service Fabric.
- Run services on specific server configurations.

![an image representing Placement constraints containing constraints for web node types, and worker node types. The network load balancer is distributing work to web nodes, who in turn distribute workloads to worker nodes](../Linked_Image_Files\3.2.3_cluster-layout-different-workloads.png)

Placement constraints are put in place in two steps:

1. Add key-value pairs to cluster nodes. You can create a Web and Worker pool by creating two VM scale sets in the cluster, and marking one VM as:

    ```'NodeType Web'```  
    (These are the blue nodes in the image.)

    and VMs in the other as: 

    ```'NodeType Worker'``` 

    (These are the green nodes in the image.)

2. Add constraint statements to your service. Creating a service that must run on the Web pool would have a constraint statement such as:

    ```'NodeType == Web'```

Service Fabric will take care of the rest. Services that were already running will be moved if necessary, and  services will be placed on the proper nodes immediately for new deployments.

> **Note**: It's important to realize that placement constraints restrict Service Fabric in its ability to balance overall cluster resource consumption. Ensure that your placement constraints are not too restrictive. If Service Fabric is unable to comply with a placement constraint, your service won't be able to run. Always create pools of multiple nodes when defining constraints.

