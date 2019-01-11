

There are two basic ways to automate the starting of a runbook, and they are:

- **schedule**
- **webhook**

A <a href="https://docs.microsoft.com/en-us/azure/automation/automation-webhooks" target="_blank"><span style="color: #0066cc;" color="#0066cc">webhook</span></a> allows you to start a particular runbook in Azure Automation through a single HTTPS request. This allows external services such as Azure DevOps, GitHub, or custom applications to start runbooks without implementing more complex solutions using the Azure Automation API.


<p style="text-align:center;"><img src="../Linked_Image_Files/1.5.4.png" alt="Flowchart of the webhook process. On the left, an External Application icon has an arrow labeled “HTTP POST” pointing to a Webhook icon. The Webhook icon has an arrow labeled “Starts runbook” pointing to a Runbook icon. The Webhook and Runbook icons are within a square labeled Automation. These three icons are in a larger square labeled Azure."></p>

### Create a Webhook
You create a web hook linked to a runbook as follows:

1. In the **Azure Portal**, open the runbook that you wish to create the webhook for.
2. In the runbook pane under **Resources** click on **Webhooks** then select **+ Add webhook**. 
3. Select **Create new webhook**. There are several values you need to configure, when finished you can click **Create**
    - **Name**: Specify any name you want for a webhook since this is not exposed to the client. It is only used for you to identify the runbook in Azure Automation.
    - **Enabled**: A webhook is enabled by default when it is created. If you set it to Disabled, then no client is able to use it.
    - **Expires**: Each webhook has an expiration date at which time it can no longer be used. The date can be modified after the webhook is created as long as the webhook is not expired
    - **URL**: The URL of the webhook is the unique address that a client calls with an HTTP POST to start the runbook linked to the webhook. It is *automatically generated when you create the webhook. You cannot specify a custom URL. The URL contains a security token that allows the runbook to be invoked by a third-party system with no further authentication. For this reason, it should be treated like a password. For security reasons, you can only view the URL in the Azure portal at the time the webhook is created. Note the URL in a secure location for future use.

        <p style="text-align:center;"><img src="../Linked_Image_Files/webhookparameters.png" alt="Graphic representing structure and flow of webhook parameter values and how the flow. starts at incoming HTTP pPOST request, with an arrow to a box containing webhook, in turn point to a box containing runbook parameter onjects."></p>
    
    > **Note**: Ensure you copy the URL of the webhook when creating it and then store it in a safe place. Once you create the webhook, you cannot retrieve the URL again.

4. Click on the **Parameters run settings (Default : Azure)** option. It allows you to do the following and has the following characteristics:
    - If the runbook has mandatory parameters, you will need to provide these mandatory parameters during creation, you are not able to create the webhook unless values are provided.
    - If there are no mandatory parameters in the runbook, there is no configuration required here.
    - The webhook must include values for any *mandatory parameters* of the runbook but may also include values for *optional parameters*.
    - When a client starts a runbook using a webhook, it cannot override the parameter values defined in the webhook.
    - To receive data from the client, the runbook can accept a single parameter called `$WebhookData `of type `[object]` that contains data that the client includes in the POST reques
    - There is no configuration of the webhook required to support the `$WebhookData` parameter

    <p style="text-align:center;"><img src="../Linked_Image_Files/createwebhook1.png" alt="Screenshot of “Create a new webhook panes. A warning explains that after creating a webhook, its URL can’t be viewed, so be sure to copy it before pressing OK. At the bottom the URL displays, with a copy button next to it."></p>

5. Click **Create** when finished

### Using a Webhook
To use a webhook after it has been created, your client application must issue an **HTTP POST** with the URL for the webhook. 

- The syntax of the webhook is in the following format:
    
    ```
       http://< Webhook Server >/token?=< Token Value >
    ```

- The client receives one of the following return codes from the POST request.

    |Code|Test|Description
    |---|---|---|
    |202|Accepted|the request was accepted and the runbook successfulyl queued|
    |400|Bad request|The request was not accepted because it hasm expired,  disabled or The token in the URL is invalid|
    |404| Not found|The request was not accepted because the webhook, runbook or account was not found|
    |500|Internal Server Error|
    

- If successful, the webhook response contains the job ID in JSON format as follows. It will contain a single job ID, but the JSON format allows for potential future enhancements.

    ```json
    {"JobIds":["< JobId >"]}
    ```

For security reasons, you can only view the URL in the Azure portal at the time the webhook is created. You should note the URL in a secure location for future use.

- The client cannot determine when the runbook job completes or its completion status from the webhook. It can determine this information using the job ID with another method such as Windows PowerShell or the Azure Automation API.


> **Note**: More details are available on the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-webhooks#details-of-a-webhook" target="_blank"><span style="color: #0066cc;" color="#0066cc">Starting an Azure Automation runbook with a webhook</span></a> page.
