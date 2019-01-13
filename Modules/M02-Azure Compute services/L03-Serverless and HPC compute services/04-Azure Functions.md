*Azure Functions* are an implementation of the Functions-as-a-Service programming model on Azure, with additional capabilities.

Azure Functions are ideal when you're only concerned with the code running your service and not with the underlying platform or infrastructure. Azure Functions are commonly used when you need to perform work in response to an event, when that work can be completed quickly, within seconds or less. For example, events can be triggered by a REST request, timer, or message from another Azure service.

![Icon representing Azure Functions, showing a lightening bolt between two angled brackets](../Linked_Image_Files/azure-functions.png)

Azure Functions scale automatically and you only accrue charges whenever a function is triggered, so functions are a solid choice when demand is variable. For example, you may be receiving messages from an IoT solution that monitors a fleet of delivery vehicles. You'll likely have more data arriving during business hours. Azure Functions can scale out to accommodate these busier times.

Furthermore, it is best practice to ensure that your functions are as stateless as possible. Stateless functions behave as if they have been restarted, every time they respond to an event. You should associate any required state information with your data instead. For example, an order being processed would likely have an associated state member. A function could process an order based on that state, update the data as required, while the function itself remains stateless.

> :information_source: If you require stateful functions, you can use the [Durable Functions Extension](https://docs.microsoft.com/en-us/azure/azure-functions/durable/durable-functions-overview) for Azure Functions or output persistent data to an Azure Storage service. For details, see the page [Functions](https://azure.microsoft.com/en-us/services/functions/).

### Azure Functions features

The following are key features of Azure Functions.

- *Choice of language*. Write functions using your language of choice, such as C#, F#, or Javascript. See [Supported languages](https://docs.microsoft.com/en-us/azure/azure-functions/supported-languages) for other options.
- *Pay-per-use pricing model*. Pay only for the time spent running your code. See the Consumption Hosting Plan Options in the [Pricing Section](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview#pricing).
- *Bring your own dependencies*. Functions supports NuGet and NPM, so you can use your favorite libraries.
- *Integrated security*. Protect HTTP-triggered functions with OAuth providers such as Azure Active Directory, Facebook, Google, Twitter, and Microsoft Account.
- *Simplified integration*. Easily leverage Azure services and software-as-a-service (SaaS) offerings. See the [Integrations Section](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview#integrations) for some examples.
- *Flexible development*. Code your functions right in the portal or set up continuous integration and deploy your code through [GitHub](https://docs.microsoft.com/en-us/azure/app-service/scripts/cli-continuous-deployment-github), [Azure DevOps Services](https://docs.microsoft.com/en-us/azure/app-service/scripts/cli-continuous-deployment-vsts), and [other supported development tools](https://docs.microsoft.com/en-us/azure/app-service/deploy-local-git).
- *Open-source* - The Functions runtime is open-source and [available on GitHub](https://github.com/azure/azure-webjobs-sdk-script).

> :information_source: You can download a free ebook, entitled [*Azure Serverless Computing Cookbook*](https://azure.microsoft.com/en-us/resources/azure-serverless-computing-cookbook/).
