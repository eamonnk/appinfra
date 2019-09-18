

Service Fabric applications consist of one or more services that work together to automate business processes. A *service* is an executable that runs independently of other services, and is composed of code, configuration, and data. Each element is separately versionable and deployable. 


<p style="text-align:center;"><img src="../Linked_Image_Files/3.1.1_application-model.png" alt="The application model has an Application box connected to a Service box, which connects to Code, Configuration, and Data boxes."></p>

#### Application and service types

<p style="text-align:center;"><img src="../Linked_Image_Files/3.1.1_Types_and_instances.png" alt="The application model has a Type box that includes Application and Service Types. This box points to the Instance box, which includes Application and Service."></p>


Creating an application instance requires an application type, which is the template that specifies which services are part of the application. This concept is similar to object-oriented programming. The application type is comparable to class definition, and the application is comparable to the instance. You can create multiple named application instances from one application type.

The same concept applies to services. The service type defines the code and configuration for the service and the endpoints that the service uses for interaction. You can create multiple service instances by using one service type. An application specifies how many instances of a service type should be created.

Both application type and service type are described through XML files. Every element of the application model is independently versionable and deployable.

#### Resource balancing


<p style="text-align:center;"><img src="../Linked_Image_Files/3.1.1_unbalanced_cluster.png" alt="The unbalance circle diagram is described in the following paragraph."></p>

While applications are running in Azure Service Fabric, they are constantly monitored for health. Service Fabric ensures that services keep running well and that the available server resources are used optimally. This means that sometimes services are moved from busy nodes to less busy nodes to keep overall resource consumption well balanced. The image above displays an imbalanced cluster. Node 2 hosts three services, while Node 1, and Nodes 3-5 are empty. Service Fabric will detect this situation and resolve it.

<p style="text-align:center;"><img src="../Linked_Image_Files/3.1.1_balanced_cluster.png" alt="The balance circle diagram is described in the following paragraph."></p>

After Service Fabric completes the balancing operation, your cluster will look like the image above. Every node now runs one service.

In reality, each node will likely run many services. Because every service is different, it's usually possible to combine services on one node to make optimal use of the server's resources. Service Fabric does all of this automatically.
