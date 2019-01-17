
Scaling ensures that you have the right amount of resources running to handle an application's needs. This can be done manually or automatically. There are two workflows for scaling Azure App services and they are:

- **Scale up**: Add additional resources to your app
    - Such as more CPU, memory, disk space, and extra features like dedicated virtual machines (VMs), custom domains and certificates, staging slots, autoscaling, and more.
    - You scale up by changing the pricing tier of the App Service plan that your app belongs to.

- **Scale out**: Increase the number of VM instances that run your app.
    - You can scale out to as many as 20 instances, depending on your pricing tier.
    - App Service Environments in Isolated tier further increases your scale-out count to 100 instances.


> **Note**: The scale settings take only seconds to apply and affect all apps in your App Service plan. They don't require you to change your code or redeploy your application.

You can also scale based on a set of pre-defined rules or schedule, and you can configure webhooks and email notifications and alerts.

### Auto Scale
Autoscale settings help ensure that you have the right amount of resources running to handle the fluctuating load of your application. You can configure Autoscale settings to be triggered based on metrics that indicate load or performance, or triggered at a scheduled date and time.

#### Metric
You can scale based on a resource metric, such as
- Scale based on CPU - You want to scale out/scale in based on a percentage CPU value.
- Scale based on custom metric - y designate a specific metric that is relevant to your app architecture i.e. You have a web front end and a API tier that communicates with the backend and you want to scale the API tier based on custom events in the front end


#### Schedule
Scale based on schedule such as:
- scale differently on weekdays Vs weekends  -  You don't expect traffic on weekends and hence you want to scale down to 1 instance on weekends.
- Scale differently during holidays - During holiday season (or specific days that are important for your business) you want to override the defaults scaling settings  and have more capacity at your disposal.


### Autoscale profiles
There are three types of Autoscale profiles which can be configured depending on what you want to achieve, and Azure evaluates which profile to execute at any given time: The profile types are:
- **Regular profile**: The most common profile. If you don’t need to scale your resource based on the day of the week, or on a particular day, you can use a regular profile.
- **Fixed date profile**: This profile is for special cases. For example, let’s say you have an important event coming up on December 26, 2017 (PST). You want the minimum and maximum capacities of your resource to be different on that day, but still scale on the same metrics
- **Recurrence profile**: This type of profile enables you to ensure that this profile is always used on a particular day of the week. Recurrence profiles only have a start time. They run until the next recurrence profile or fixed date profile is set to start.

#### Example
An example of how this looks in an Azure Resource Manager template is. This Autoscale setting has:
    - One profile.
    - Two metric rules in this profile: one for scale out, and one for scale in.
        - The scale-out rule is triggered when the virtual machine scale set's average percentage CPU metric is greater than 85 percent for the past 10 minutes.
        - The scale-in rule is triggered when the virtual machine scale set's average is less than 60 percent for the past minute.

```json
{
  "id": "/subscriptions/s1/resourceGroups/rg1/providers/microsoft.insights/autoscalesettings/setting1",
  "name": "setting1",
  "type": "Microsoft.Insights/autoscaleSettings",
  "location": "East US",
  "properties": {
    "enabled": true,
    "targetResourceUri": "/subscriptions/s1/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachineScaleSets/vmss1",
    "profiles": [
      {
        "name": "mainProfile",
        "capacity": {
          "minimum": "1",
          "maximum": "4",
          "default": "1"
        },
        "rules": [
          {
            "metricTrigger": {
              "metricName": "Percentage CPU",
              "metricResourceUri": "/subscriptions/s1/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachineScaleSets/vmss1",
              "timeGrain": "PT1M",
              "statistic": "Average",
              "timeWindow": "PT10M",
              "timeAggregation": "Average",
              "operator": "GreaterThan",
              "threshold": 85
            },
            "scaleAction": {
              "direction": "Increase",
              "type": "ChangeCount",
              "value": "1",
              "cooldown": "PT5M"
            }
          },
    {
            "metricTrigger": {
              "metricName": "Percentage CPU",
              "metricResourceUri": "/subscriptions/s1/resourceGroups/rg1/providers/Microsoft.Compute/virtualMachineScaleSets/vmss1",
              "timeGrain": "PT1M",
              "statistic": "Average",
              "timeWindow": "PT10M",
              "timeAggregation": "Average",
              "operator": "LessThan",
              "threshold": 60
            },
            "scaleAction": {
              "direction": "Decrease",
              "type": "ChangeCount",
              "value": "1",
              "cooldown": "PT5M"
            }
          }
        ]
      }
    ]
  }
}

```

> **Note**: See some best auto-scale best practices on the page <a href="https://docs.microsoft.com/en-us/azure/azure-monitor/platform/autoscale-best-practices" target="_blank"><span style="color: #0066cc;" color="#0066cc">Best practices for Autoscale</span></a> page.
