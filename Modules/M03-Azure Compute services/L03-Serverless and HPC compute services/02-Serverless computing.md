
*Serverless computing* is a cloud-hosted execution environment that runs your code, yet abstracts the underlying hosting environment. You create an instance of the service and you add your code. No infrastructure configuration or maintenance is required, or even allowed. 

You configure your serverless apps to respond to events. An event could be a REST endpoint, a periodic timer, or even a message received from another Azure service. The serverless app runs only when it's triggered by an event.

Scaling and performance are managed automatically, and you're billed only for the exact resources you use. You don't even need to reserve resources.

### Serverless definition
The core characteristics that define a serverless service are:

- Service is consumption based. The service provisions resources on demand, and you only pay for what you use. Billing is typically calculated by the number of function calls, code execution time, and memory used. (Supporting services such as networking and storage could be charged separately.)

- Low management overhead. Because serverless service is cloud-hosted, you won't need to be patching VMs or have a burdensome operational workflow. Serverless services provide for the full abstraction of servers, so developers can just focus on their code. There are no distractions around server management, capacity planning, or availability.

- Auto-scale. Compute execution can be in milliseconds, so it's almost instant. It provides for event-drive scalability. Application components react to events and trigger in near real-time with virtually unlimited scalability.


### Benefits of the serverless computing model
The benefits of serverless computing are:

- Efficiency:
    - Serverless computing can result in a shorter times for the product to get to market as  developers can focus more on their applications and customer value.
    - Fixed costs are converted to variable costs, and you are only paying for what is consumed.
    - Cost savings are realized by the variable costs model.

- Focus:
    - You can focus on solving business problems, and not on allocating time to defining and carrying out operational tasks such as VM management.
    - Developers can focus on their code. There are no distractions around server management, capacity planning, or availability.


- Flexibility:
    - Serverless computing provides a simplified starting experience.
    - Easier pivoting means more flexibility.
    - Experimentation is easier as well.
    - You can scale at your pace.
    - Serverless computing is a natural fit for microservices.

### Serverless Azure services
Some of the serverless services in Azure are listed in the following table.

| Azure service | Functionality |
|---|---|
|Azure Event grid | Manage all events that can trigger code or logic|
|Azure Functions | Execute code based on events you specify|
|Azure Automation | Automate tasks across Azure and hybrid environments|
|Azure Logic Apps | Design workflows and orchestrate processes|

The service we're interested in from a DevOps and compute point of view is Azure Functions. 

