

*Azure Functions* are Azure's implementation of the Functions as a service programming model, with additional capabilities. 

<p style="text-align:center;"><img src="../Linked_Image_Files/azurefunctions.png" width="100" height="100" alt="Image representing Azure Functions"></p>

Azure Functions are ideal when you're only concerned with the code running your service and not the underlying platform or infrastructure. Azure Functions are commonly used when you need to perform work in response to an event—often via a REST request, timer, or message from another Azure service—and when that work can be completed quickly, within seconds or less. 

Azure Functions scale automatically and charges accrue only when a function is triggered, so they're a solid choice when demand is variable. For example, you may be receiving messages from an IoT solution that monitors a fleet of delivery vehicles. You'll likely have more data arriving during business hours. Azure Functions can scale out to accommodate these busier times.

Furthermore, Azure Functions are stateless; they behave as if they're restarted every time they respond to an event. This is ideal for processing incoming data. And if state is required, they can be connected to an Azure storage service. See <a href="https://azure.microsoft.com/en-us/services/functions/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Functions</span></a> for more details.


### Azure Functions features
Some key features of Azure Functions are:
- *Choice of language* - Write functions using your choice of C#, F#, or Javascript. See Supported languages for other options.
- *Pay-per-use pricing model* - Pay only for the time spent running your code. See the Consumption hosting plan option in the pricing section. 
- *Bring your own dependencies* - Functions supports NuGet and NPM, so you can use your favorite libraries. 
- *Integrated security* - Protect HTTP-triggered functions with OAuth providers such as Azure Active Directory, Facebook, Google, Twitter, and Microsoft Account. 
- *Simplified integration* - Easily leverage Azure services and software-as-a-service (SaaS) offerings. See the integrations section for some examples. 
- *Flexible development* - Code your functions right in the portal or set up continuous integration and deploy your code through GitHub, Azure DevOps Services, and other supported development tools. 
- *Open-source* - The Functions runtime is open-source and available on GitHub. 

> **Note**: You can download a free ebook, entitled Azure Serverless Computing cookbook, from the  <a href="https://azure.microsoft.com/en-us/resources/azure-serverless-computing-cookbook/ " target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Serverless Computing Cookbook</span></a> page.
