**IaaS**
With IaaS, you provision the VMs that you need along with associated network and storage components. You then deploy whatever software and applications you want onto those VMs. This model is the closest to a traditional on-premises environment except that Microsoft manages the infrastructure. You still manage the individual VMs.


**PaaS** 
Paas provides a managed hosting environment where you can deploy your application without needing to manage VMs or networking resources. For example, instead of creating individual VMs, you specify an instance count, and the service will provision, configure, and manage the necessary resources. Azure App Service is an example of a PaaS service.

There is a spectrum from IaaS to pure PaaS. For example, Azure VMs can auto-scale by using VM Scale Sets. This automatic scaling capability isn't strictly with PaaS, but it's the type of management feature that might be found in a PaaS service.

**FaaS** 
FaaS goes even further in removing the need to worry about the hosting environment. Instead of creating compute instances and deploying code to those instances, you simply deploy your code, and the service automatically runs it. You don’t need to administer the compute resources, because the services make use of serverless architecture, and seamlessly scale up or down to whatever level necessary to handle the traffic. Azure Functions are a FaaS service.

When comparing the three environments, remember that:

- IaaS gives the most control, flexibility, and portability. 
- FaaS provides simplicity, elastic scale, and potential cost savings because you pay only for the time your code is running. 
- PaaS falls somewhere between the two. 

In general, the more flexibility a service provides, the more responsible you are for configuring and managing the resources. FaaS services automatically manage nearly all aspects of running an application, while IaaS solutions require you to provision, configure, and manage the VMs and network components you create.
