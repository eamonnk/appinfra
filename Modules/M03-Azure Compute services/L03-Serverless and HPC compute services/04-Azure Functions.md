

*Azure Functions* are Azure's implementation of the FaaS programming model, with additional capabilities. 

<p style="text-align:center;"><img src="../Linked_Image_Files/azure-functions.png" width="100" height="100" alt="Azure Functions icon."></p>

Azure Functions are ideal when you're only concerned with the code running your service and not the underlying platform or infrastructure. Azure Functions are commonly used when you need to perform work in response to an event (often via a REST request, timer, or message from another Azure service), and when that work can be completed quickly, within seconds or less. 

Azure Functions scale automatically, and charges accrue only when a function is triggered, so they're a good choice when demand is variable. For example, you might be receiving messages from an Internet of Things (IoT) solution that monitors a fleet of delivery vehicles. You'll likely have more data arriving during business hours. Azure Functions can scale out to accommodate these busier times.

Furthermore, Azure Functions are stateless; they behave as if they're restarted every time they respond to an event. This is ideal for processing incoming data. And if state is required, they can be connected to an Azure storage service. See <a href="https://azure.microsoft.com/en-us/services/functions/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Functions</span></a> for more details.


### Azure Functions features
Some key features of Azure Functions are:

- Choice of language. Write functions using your choice of C#, F#, or JavaScript. 
- Pay-per-use pricing model. Pay only for the time spent running your code. 
- Bring your own dependencies. Functions support NuGet and NPM, so you can use your favorite libraries. 
- Integrated security. Protect HTTP-triggered functions with OAuth providers such as Azure AD, Facebook, Google, Twitter, and your Microsoft Account. 
- Simplified integration. Easily leverage Azure services and software-as-a-service (SaaS) offerings. 
- Flexible development. Code your functions directly in the portal, or set up continuous integration and deploy your code through GitHub, Azure DevOps Services, and other supported development tools. 
- Open-source. The Functions runtime is open-source and available on GitHub. 

> **Note**: You can download the free eBook, *Azure Serverless Computing cookbook*, from the  <a href="https://azure.microsoft.com/en-us/resources/azure-serverless-computing-cookbook/ " target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Serverless Computing Cookbook</span></a> webpage.
