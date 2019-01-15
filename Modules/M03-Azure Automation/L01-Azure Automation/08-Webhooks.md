The following are two basic ways to automate the starting of a runbook.

- [Schedule](HTTP://docs.microsoft.com/en-us/azure/automation/automation-schedules). Starts a runbook in Azure Automation at a specified time, either by running it once or on a reoccurring hourly or daily schedule.
- [Webhook](HTTP://docs.microsoft.com/en-us/azure/automation/automation-webhooks). Allows you to start a runbook in Azure Automation with a single HTTP POST request. External services such as Azure DevOps, GitHub, and other applications can start runbooks without the need to implement complex solutions using the Azure Automation API.

<p style="text-align:center;"><img src="../Linked_Image_Files/1.5.4.png" alt="Flowchart of the webhook process. On the left, an icon representing an 'External Application' is shown. An arrow labeled 'HTTP POST' points eastwards towards an icon representing a 'Webhook event'. The Webhook event icon contains another arrow labeled 'Starts runbook', which points eastwards toward an icon representing a 'Runbook'. The Webhook event and Runbook icons are enclosed by a rectangle labeled 'Automation'. All three icons and the rectangle are enclosed within a larger rectangle labeled 'Azure'. The label for the outer rectangle is shown beside an icon of a cloud."></p>

> :information_source: For information about other methods for starting a runbook see the page [Starting a runbook in Azure Automation](HTTP://docs.microsoft.com/en-us/azure/automation/automation-starting-a-runbook)

### Create a Webhook

The following describes how to create a Webhook, and how to link the Webhook to an existing runbook.

1. In the Azure Portal, open the runbook that you wish to create the Webhook for.
2. In the **Runbook Pane** under **Resources** choose **Webhooks**, then select **+ Add webhook**.
3. Select **Create new webhook**. You need to configure the following values, and when you have finished select **Create**.
    - **Name**. Specify the name you want for the Webhook. This name is not exposed to the client, so you can choose whatever name you wish to use. The name is only used by you to identify the runbook in Azure Automation.
    - **Enabled**. A Webhook is enabled by default when it is created. If you set this option to *Disabled*, then no client can use the Webhook.
    - **Expires**. Each Webhook has an expiration date, after which it can no longer be used. The date can be modified after the Webhook is created, as long as the Webhook has not expired already.
    - **URL**. The URL of the Webhook is a unique address. A client calls the URL with an HTTP POST request to start the runbook linked to the Webhook. The Webhook URL is generated automatically when you create the Webhook. You cannot specify a custom URL. The URL contains a security token that allows the runbook to be invoked by a third-party systems with no further authentication. For this reason, the URL should be treated like a password. For security reasons, you can only view the URL in the Azure portal at the time the Webhook is created. You should note the URL and store it in a secure location for future use.

      <p style="text-align:center;"><img src="../Linked_Image_Files/webhookparameters.png" alt="Graphic representing the structure and flow of a Webhook HTTP POST REQUEST process triggering the start of a Runbook. The image shows parameter values within POST REQUEST and within the Webhook data object, and how they relate to each other. On the left, an arrow labelled 'HTTP POST' points eastwards to a square. The square represents the contents of the HTTP request. The square contains parameter values of incoming HTTP POST request. Another arrow points eastwards from the square towards a second square. The second square contains parameter values of the Webhook data object which triggers the start of the runbook."></p>

      > :information_source: It is very important to ensure that you copy the URL of the Webhook when you create it. Store the URL in a safe place. The URL contains an authentication token. Once you have created the Webhook, you cannot retrieve the URL again.

4. Choose the **Parameters run settings (Default : Azure)** option. The following describes what the 'Parameters run settings (Default : Azure)' option allows you to do, and its characteristics.
    - If the runbook has mandatory parameters, you will need to provide these mandatory parameters during creation. You cannot create the Webhook unless you provide these values.
    - If there are no mandatory parameters in the runbook, no configuration is necessary here.
    - The Webhook must include values for any *mandatory parameters* of the runbook, but may also include values for *optional parameters*.
    - When a client starts a runbook from a Webhook, it cannot override the parameter values defined in the runbook.
    - To receive data from the client, the runbook can accept a parameter called `$WebhookData` of type `[object]`. The `$WebhookData` object contains data that the client includes in the HTTP POST request.
    - No configuration of the Webhook is required to support the `$WebhookData` parameter.

    <p style="text-align:center;"><img src="../Linked_Image_Files/createwebhook1.png" alt="Screenshot of the 'Create a new webhook panes'. A warning is shown which explains that after creating a Webhook, its URL cannot be viewed. The warning message sates 'be sure to copy it before pressing OK'. The URL is displayed, with a copy button next to it."></p>

5. When you have finished choose **Create**.

### Using a Webhook

To use a Webhook after it has been created, your client application must issue an HTTP POST request with the URL for the Webhook.

- The Webhook URL uses the following syntax.

  ```html
    http://< Webhook Server >/token?=< Token Value >
  ```

- The client receives one of the following return codes from the Webhook HTTP POST request.

    |Code | Test | Description
    |-----|------|------------|
    | 202 | Accepted | The request was accepted and the runbook was queued successfully. |
    | 400 | Bad request | The request was not accepted because it has expired, been disabled or the authentication token in the URL is invalid. |
    |404 | Not found | The request was not accepted because the Webhook, runbook or account was not found. |
    |500 | Internal Server Error | The URL was valid, but an error occurred. Please resubmit the request. |

- If the HTTP POST request is successful, the Webhook response will contain the `job ID` in JSON format. The Webhook response will contain a single `job ID`, but using the JSON format allows for potential future enhancements. The JSON response is formatted as follows:

```json
  { "JobIds" : [ "< JobId > " ] }
```

- The client cannot determine when the runbook job completes or its completion status from the Webhook. A client can determine this information by using the `job ID` with another method, with Windows PowerShell or the Azure Automation API for example.

> :information_source: Details about the properties that you must configure for a Webhook are available on the page [Starting an Azure Automation runbook with a Webhook](HTTP://docs.microsoft.com/en-us/azure/automation/automation-webhooks#details-of-a-webhook).
