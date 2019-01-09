

*Idempotence* is a mathematical term that can be used in the context of infrastructure and configuration as code, where it is the ability to apply one or more operation against a resource, resulting in the same outcome. 

For instance, if I run a script on a system it should have the same outcome regardless of the number of times I execute the script, rather than erroring out, or performing duplicate actions, and regardless of the environment’s starting state.

In essence if you apply a deployment to a set of resources 1000 times, you will end up with the same result after each application of the script or template.

<p style="text-align:center;"><img src="../Linked_Image_Files/idempotency.png" alt="A circle with  i,ages representing a script followed by a line to an image representing an application in its final state, and this continues in a circle."></p>

*Idempotency* can be achieved by:

- automatically configuring, and re-configuring, an existing set of resources.

    **or** 

- discarding the existing resources and recreating a fresh environment.

When defining infrastructure and configuration as code It would be best practice to build those scripts and templates in such as way as to embrace *idempotency*, this is especially so when dealing with cloud services where resources and applications can be scaled in and out regularly, and new instances of services can be started up to provide elasticity in a service. Avoidance of *idempotency* would not be a best practice.



> **Note**: <p> You can read more about <i>idempotence</i> in general and in the context of Azure on the page <a href="https://www.wintellect.com/idempotency-for-windows-azure-message-queues/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Idempotency for Windows Azure Message Queues</span>.</p></a>