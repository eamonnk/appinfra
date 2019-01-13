*Placement Constraints* can be used to:
- Isolate workloads from each other.
- 'Lift and shift' an existing N-tier application into Azure Service Fabric.
- Run services on specific server configurations.

![Image representing Placement Constraints. The image depicts constraints for 'web node type', and for 'worker node type'. The images shows the constraints applied to a network load balancer, distributed among web worker nodes. The constraints are, in turn, distributed to the workloads under the web worker nodes](../Linked_Image_Files\3.2.3_cluster-layout-different-workloads.png)

Placement Constraints are put in place in two steps.

:one: Add key-value pairs to cluster nodes. Create a *Web* and *Worker* pool by creating two VM scale sets in the cluster. Mark VMs in one scale set as ```NodeType Web``` (shown as blue nodes in the image). Then, mark VMs in the other as ```NodeType Worker``` (show as green nodes in the image.)

:two: Add constraint statements to your service. Creating a service that must run on the Web pool would have a constraint statement like this: ```NodeType == Web```

Service Fabric will take care of the rest. Services that were already running will be moved, if needed. For new deployments, services will be placed on the proper nodes immediately.

> :information_source: It's important to realize that Placement Constraints can restrict Service Fabric's ability to balance overall cluster resource consumption. Make sure that your Placement Constraints are not too restrictive. If Service Fabric is unable to comply with a Placement Constraint, your service will not run. Always create pools of multiple nodes when defining your Placement Constraints.
