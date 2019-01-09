In the context of Infrastructure and Configuration as Code, *Idempotency* is the application of one or more operations, against a resource, which result in the same outcome.

> For example, idempotency requires that running a script on a system should result in the same outcome, regardless of the number of times I execute the script, without erroring out or performing duplicate actions, despite the environment’s starting state.

In essence, with idempotency, using a script or template to apply a deployment to a set of resources, innumerable times, should produce the same result after each application of the script or template.

<p style="text-align:center;"><img src="../Linked_Image_Files/idempotency.png" alt="A image depicting the cyclical process from the execution of a script to the final state of a software application, with symbols representing scripts and software applications located at fixed intervals around a circle."></p>

Idempotency can be achieved by either *one* of the following:
- Automatically configuring, and re-configuring, an existing set of resources.
- Discarding the existing resources and recreating a fresh environment.

When defining infrastructure and configuration as code It would be best practice to build those scripts and templates in such as way as to embrace *idempotency*, this is especially so when dealing with cloud services where resources and applications can be scaled in and out regularly, and new instances of services can be started up to provide elasticity in a service. Avoidance of *idempotency* would not be a best practice.

> :information_source: You can read more about *idempotence* on the page [Idempotency for Windows Azure Message Queues](https://www.wintellect.com/idempotency-for-windows-azure-message-queues/).
