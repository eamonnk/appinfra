*Azure DevTest Labs* enables you to quickly set up an environment for your team (for example: development environment, test environment) in the cloud. A lab owner creates a lab, provisions Windows, or Linux virtual machines, installs the necessary software and tools, and makes them available to lab users. Lab users connect to virtual machines (VMs) in the lab, and use them for their day-to-day work, short-term projects. Once users start utilizing resources in the lab, a lab admin can analyze cost and usage across multiple labs, and set overarching policies to optimize your organization or team's costs.


> **Note**: *Azure DevTest Labs* is being expanded with new types of labs, namely *Azure Lab Services*. *Azure Lab Services* lets you create managed labs, such as classroom labs. The service itself handles all the infrastructure management for a managed lab, from spinning up VMs to handling errors, and scaling the infrastructure. The managed labs are currently in preview. Once the preview ends, the new lab types and existing DevTest Labs come under the new common umbrella name of *Azure Lab Services* where all lab types continue to evolve.

### Usage scenarios
The following are some common use cases for using *Azure DevTest Labs*:

- **Use DevTest Labs for development environments** - host development machines for developers.
    - Enable developers to quickly provision their development machines on demand.
    - Provision Windows and Linux environments using reusable templates and artifacts.
    - Developers can easily customize their development machines whenever needed

- **Use DevTest Labs for test environments** -  host machines for testers
    - Testers can test the latest version of their application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.
    - Testers can scale up their load testing by provisioning multiple test agents.
    - Administrators can control costs by ensuring that testers cannot get more VMs than they need for testing and VMs are shut down when not in use.

- **Integrate DevTest Labs with Azure DevOps CI/CD pipeline** - You can use the *Azure DevTest Labs Tasks* extension that's installed in *Azure DevOps* to easily integrate your CI/CD build-and-release pipeline with Azure DevTest Labs. The extension installs three tasks: 
    - Create a VM
    - Create a custom image from a VM
    - Delete a VM 

    The process makes it easy to, for example, quickly deploy a "golden image" for a specific test task and then delete it when the test is finished.


> **Note**: For more information on DevTest Labs see the 
<a href="https://docs.microsoft.com/en-us/azure/lab-services/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Lab Services Preview and Azure DevTest Labs Documentation</span></a>