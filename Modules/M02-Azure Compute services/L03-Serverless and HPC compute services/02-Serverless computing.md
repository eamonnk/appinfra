*Serverless computing* is a cloud-hosted execution environment that runs your code but abstracts the underlying hosting environment. You create an instance of the service and you add your code. No infrastructure configuration or maintenance is required, or even allowed. 

You configure your serverless apps to respond to events. An event could be a REST endpoint, a periodic timer, or even a message received from another Azure service. The serverless app runs only when it's triggered by an event.

Scaling and performance are handled automatically, and you are billed only for the exact resources you use. You don't even need to reserve resources.


### Serverless definition
The core characteristics that define a serverless service are:

1. Service is consumption based: The service provisions resources on demand and you only pay for what you use. Billing is typically calculated by the number of function calls, code execution time, and memory used (supporting services such as networking and storage may be charged separately.)

2. Really low management overhead: You shouldn't be patching VMs or have a burdensome operational workflow. Server less services provide for the full abstraction of servers : focus only on your application code. Developers can just focus on their code. There are no distractions around server management, capacity planning, availability

3. Auto-scale: execution of compute can be in the order of milliseconds, so can be near instant. It provides for event-drive scalability. Application components react to events and triggers in near real-time with virtual unlimited scalability.


### Benefits of Serverless computing model
The benefits that serverless computing can be defined as follows:

- *Efficiency*:
    - Can result in a shorter time to market as you can focus more on your application and customer value
    - Fixed costs converted to variable costs and only paying for what is consumed
    - Cost savings

- *Focus*:
    - Can focus on solving business problems, not allocating time to defining and carrying out operational tasks, such as VM management.
    - Developers can just focus on their code. There are no distractions around server management, capacity planning, availability


- *Flexibility*:
    - Simplified starting experience
    - easier pivoting means more flexibility
    - Easier experimentation
    - Scale at your pace, don't bet the farm on day 1
    - Natural for for microservices

### Serverless Azure services
Some of the serverless services in Azure are:

| Azure service | Functionality |
|---|---|
|**Event Grid** | Manage all events that can trigger code or logic|
|**Functions** | Execute code based on events you specify|
|**Automation** | Automate task across Azure and hybrid environments|
|**Logic Apps** | Design workflows and orchestrate processes|

The service we're interested in from a DevOps and compute point of view is **Azure Functions**.
