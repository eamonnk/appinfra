

Developing applications for use on Service Fabric has a number of options available.

### Windows

Azure Service Fabric comes with an SDK and development tool support. Development for Windows clusters can be done in C#, by using Microsoft Visual Studio 2015 and 2017.

### Linux
Developing Java-based services for Linux clusters is probably easiest to do by using <a href="https://www.eclipse.org/neon/ " target="_blank"><span style="color: #0066cc;" color="#0066cc">Eclipse Neon</span></a> but it's also possible to program in C# using .NET Core and Visual Studio Code.


> *Note*: If you are interested in developing Service Fabric applications, you should look at the Microsoft Virtual Academy course *Building Microservices Applications on Azure Service Fabric*.
>Instructors: Jeffrey Richter, Subramanian Ramaswamy, Mark Fussell
>https://mva.microsoft.com/en-US/training-courses/building-microservices-applications-on-azure-service-fabric-16747

> You might also be interested in the online course [DEVOPS200.9x: Architecting Distributed Cloud Applications](https://www.edx.org/course/architecting-distributed-cloud-microsoft-devops200-9x-1), available on edx.org.

### Programming models

There are four different programming models that you can choose from to create an Service Fabric application.

1. **Reliable Services**

    Reliable Services is a framework to create services that use specific features that Service Fabric provides. One important feature is a distributed data storage mechanism. Others are custom load and health reporting, and automatic endpoint registration, which enables discoverability and interaction between services. There are two distinct types of Reliable Services that you can create, stateless services and stateful services.

    - Stateless services are intended to perform operations that do not require that an internal state be kept. Examples are services that host ASP.NET Web APIs, or services that autonomously process items read from a Service Bus Queue.

    - Stateful services keep internal state. This state is automatically stored redundantly across multiple nodes, for availability and error recovery. The data stores are called Reliable Collections.


2. **Reliable Actors**

    Reliable Actors is a framework built on top op Reliable Services that implements the Virtual Actors design pattern. An Actor encapsulates a small piece of state and behavior. One example is the so-called Digital Twins, where an Actor represents the state and abilities of a device in the real world. Many Internet Of Things (IoT) applications use the Actor model to represent the things.

    The state of an Actor can be volatile, or it can be kept in the distributed store. This store can be memory based or on disk.

3. **Guest executables**

    You can also package and run existing applications as a Service Fabric (stateless) services.
    This way, Applications are made highly available. The platform ensures that the instances of an application are running. Applications can also be upgraded with no downtime. Service Fabric can automatically roll back the deployment if problems are reported during an upgrade.

    Finally, Service Fabric enables you to run multiple applications together in a cluster, which reduces the need for hardware resources.

    > **Note**: It's important to note that you cannot use some of the platform capabilities like the Reliable Collections when using Guest executables.

​
4. **Containers**

    Containers can be run in a way that is similar to running guest executables. What’s different is that Service Fabric can restrict resource consumption (CPU and memory, for example) per container. Limiting resource consumption per service enables you to achieve even higher densities on your cluster.
