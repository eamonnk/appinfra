


Service Fabric applications consist of one or more services that work together to automate business processes. A service is an executable that runs independently of other services, and it is composed of code, configuration, and data. Each element is separately versionable and deployable. 

![The application model has an Application box connected to a Service box. Service connects to Code, Configuration, and Data.](../../Linked_Image_Files\3.1.1_application-model.png)


#### Application types and service types

![The application model has a Type box including Application and Service Types pointing to the Instance box pointing to Application and Service.](../../Linked_Image_Files\3.1.1_Types_and_instances.png)

Creating an application instance requires an application type, which is the this is the template that specifies which services are part of the application. This concept is similar to object-oriented programming. The application type is like the class definition, and the application is like the instance. Multiple named application instances can be created from one application type.

The same concept applies to services. The service type defines the code and configuration for the service, and the endpoints that the service uses for interaction. Multiple service instances can be created by using one service type. An application specifies how many instances of a service type should be created.

Both application type and service type are described through XML files. Every element of the application model is independently versionable and deployable.

#### Resource balancing

![The unbalance circle diagram is described below.](../../Linked_Image_Files\3.1.1_unbalanced_cluster.png)

While applications run in Azure Service Fabric, they are constantly monitored for health. Service Fabric ensures that services keep running well and that the available server resources are used optimally. This means that sometimes services are moved from busy nodes to less busy nodes, to keep overall resource consumption well balanced. The image above shows an imbalanced cluster. Node 2 hosts three services while Node 1 and Node 5 are empty. Service Fabric will detect this situation and resolve it.

![The balance circle diagram is described below.](../../Linked_Image_Files\3.1.1_balanced_cluster.png)

After Service Fabric completes the balancing operation, your cluster will look like the image above. Every node now runs one service.

In reality, each node will likely run many services. Because every service is different, it's usually possible to combine services on one node to make optimal use of the server's resources. All this is done automatically by Service Fabric.