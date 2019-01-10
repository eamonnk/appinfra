Certain combinations of resources sometimes need to be provisioned in a particular order. For example, it makes sense to create a SQL server before initializing a SQL database. In these kinds of relationships, one resource is *dependent* on another resource. You can define dependencies with the *dependsOn* key, within your template, or by using the *reference* function.

Azure Resource Manager can evaluate the dependencies between resources, and deploy them according to their dependent order. Azure Resource Manager otherwise deploys independent resources in parallel. You only need to define dependencies for resources that are deployed in the same template.

### The *dependsOn* element

Within your template, the `dependsOn` key allows you to classify one resource as dependent on one or more resources. The value of the dependsOn key can be set with a comma-separated, list of resource names.

![Screenshot of a section of JSON from an Azure Resource Manager template with the dependOn key-value pair highlighted](../Linked_Image_Files/dependson.png) 

### Circular dependencies

*Circular Dependency* is a loop caused by deploying dependent resources in the wrong order. Circular Dependency prevents Azure Resource Manager from deploying resources successfully. Azure Resource Manager tries to identify Circular Dependencies during template validation.

However, if you receive an error stating that a circular dependency exists, you should evaluate your template, reorder any incorrectly sequenced dependencies, and remove unnecessary dependencies. If removing dependencies doesn't work, you can resolve circular dependency errors by moving some deployment operations into child resources, so that they are deployed *after* the resources with circular dependency issues.
