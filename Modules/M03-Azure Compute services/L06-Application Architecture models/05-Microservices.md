
A *microservices* architecture consists of a collection of small, autonomous services. Each service is self-contained and should implement a single business capability.

<p style="text-align:center;"><img src="../Linked_Image_Files/microservice.png" alt="A representation of the microservices architectural model."></p>


In some ways, microservices are the natural evolution of Service Oriented Architectures (SOA), but there are differences between microservices and SOA. Here are some defining characteristics of a microservice:

- In a microservices architecture, services are small, independent, and loosely coupled.
- Each service is a separate codebase, which you can manage with a small development team.
- You can deploy services independently. A team can update an existing service without rebuilding and redeploying the entire application.
- Services are responsible for persisting their own data or external state. This differs from the traditional model, where a separate data layer manages data persistence.
- Services communicate with each other by using well-defined APIs. However, internal implementation details of each service are hidden from other services.
- Services don't need to share the same technology stack, libraries, or frameworks.

### When to use this architecture
You should consider using this architecture for:
- Large applications that require a high release velocity.
- Complex applications that need to be highly scalable.
- Applications with rich domains or many subdomains.
- An organization that consists of small development teams.

### Benefits
The benefits of this architecture are:

- Independent deployments. You can update a service without redeploying the entire application. You also can roll back or roll forward an update if something goes wrong. Bug fixes and feature releases are more manageable and less risky.
- Independent development. A single development team can build, test, and deploy a service. The result is continuous innovation and a faster release cadence.
- Small, focused teams. Teams can focus on one service. The smaller scope of each service makes the code base easier to understand, and it's easier for new team members to ramp up.
- Fault isolation. If a service goes down, it won't take out the entire application. However, that doesn't mean you get resiliency for free. You still need to follow resiliency best practices and design patterns. 
- Mixed technology stacks. Teams can pick the technology that best fits their service.
- Granular scaling. Services can be scaled independently. At the same time, the higher density of services per VM means that VM resources are fully utilized. Using placement constraints, a services can be matched to a VM profile, including high CPU and high memory.
