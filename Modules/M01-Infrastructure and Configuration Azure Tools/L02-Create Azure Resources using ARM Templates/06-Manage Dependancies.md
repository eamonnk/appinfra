
For any given resource, there can be other resources that must exist before the resource is deployed. For example, a SQL server must exist before attempting to deploy a SQL database. You can define this relationship by marking one resource as *dependent* on the other resource. You define a dependency with the **dependsOn** element, or by using the **reference** function. 

Resource Manager evaluates the dependencies between resources, and deploys them in their dependent order. When resources aren't dependent on each other, Resource Manager deploys them in parallel. You only need to define dependencies for resources that are deployed in the same template.

### The `dependsOn` element
Within your template, the **dependsOn** element enables you to define one resource as a dependent on one or more resources. Its value can be a comma-separated list of resource names. 

<p style="text-align:center;"><img src="../Linked_Image_Files/dependson.png" alt="A section of Resource manager template code with the dependOn section highlighted."></p>

### Circular dependencies
A circular dependency means there is a problem with dependency sequencing, preventing Resource manager deploying the resources, resulting in the deployment going around in a loop and unable to proceed. Resource Manager identifies circular dependencies during template validation. If you receive an error stating that a circular dependency exists, evaluate your template to see if any dependencies aren't needed and can be removed. 

If removing dependencies doesn't work, you can avoid circular dependencies by moving some deployment operations into child resources that are deployed after the resources that have the circular dependency.