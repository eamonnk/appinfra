
Scaling ensures that you have the right amount of resources running to manage an application's needs. Scaling can be done manually or automatically. 

There are two workflows for scaling Azure App services:

- Scale up. Add additional resources to your app such as more CPU, memory, disk space. You can also add extra features such as dedicated VMs, custom domains and certificates, staging slots, and autoscaling. 
    - To scale up, you will need to change the pricing tier of your App Service plan.

- Scale out. Increase the number of VM instances that run your app. 
    - You can scale out to as many as 20 instances, depending on your pricing tier. 
    - App Service environments in Isolated tier further increases your scale-out count to 100 instances.


> **Note**: The scale settings take seconds to apply and affect all apps in your App Service plan. They don't require you to change your code or redeploy your application.

You can also scale based on a set of predefined rules or schedule, and configure webhooks and email notifications and alerts.

### Autoscale
Autoscale settings help ensure that you have the right amount of resources running to manage the fluctuating load of your application. You can configure Autoscale settings to trigger based on metrics that indicate load or performance, or at a scheduled date and time. 

#### Metric
You can scale based on a resource metric, such as:

- Scale based on CPU. You want to scale out or scale in based on a percentage CPU value.

- Scale based on custom metric. To scale based on a custom metric, you designate a specific metric that is relevant to your app architecture. For example, you might have a web front end and an API tier that communicates with the backend, and you want to scale the API tier based on custom events in the front end.


#### Schedule 
You can scale based on a schedule as well. For example, you can:

- Scale differently on weekdays Vs weekends. You don't expect traffic on weekends, hence you want to scale down to 1 instance on weekends.
- Scale differently during holidays. During holidays or specific days that are important for your business, you might want to override the defaults scaling settings  and have more capacity at your disposal.


### Autoscale profiles
There are three types of Autoscale profiles that you can configure depending on what you want to achieve. Azure then evaluates which profile to execute at any given time. The profile types are:

- Regular profile. This is the most common profile. If you don’t need to scale your resource based on the day of the week, or on a particular day, you can use a regular profile. 
- Fixed date profile. This profile is for special cases. For example, let’s say you have an important event coming up on December 26, 2019 (PST). You want the minimum and maximum capacities of your resource to be different on that day, but still scale on the same metrics.
- Recurrence profile. This type of profile enables you to ensure that this profile is always used on a particular day of the week. Recurrence profiles only have a start time. They run until the next recurrence profile or fixed date profile is set to start.

#### Example
An example of how this looks in an Azure Resource Manager template is an Autoscale setting with one profile, as below:

- There are two metric rules in this profile: one for scale out, and one for scale in.
    - The scale-out rule is triggered when the VM scale set's average percentage CPU metric is greater than 85 percent for the past 10 minutes.
    - The scale-in rule is triggered when the VM scale set's average is less than 60 percent for the past minute.

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

> **Note**: You can review some best auto-scale best practices on the <a href="https://docs.microsoft.com/en-us/azure/azure-monitor/platform/autoscale-best-practices" target="_blank"><span style="color: #0066cc;" color="#0066cc">Best practices for Autoscale</span></a> page.
