
You can automate the process of starting a runbook either by scheduling it, or by using a webhook.

A *webhook* allows you to start a particular runbook in Azure Automation through a single HTTPS request. This allows external services such as Azure DevOps, GitHub, or custom applications to start runbooks without implementing more complex solutions using the Azure Automation API 
(More information about webhooks is available at <a href="https://docs.microsoft.com/en-us/azure/automation/automation-webhooks" target="_blank"><span style="color: #0066cc;" color="#0066cc">Starting an Azure Automation runbook with a webhook</span></a>.)

<p style="text-align:center;"><img src="../Linked_Image_Files/1.5.4.png" alt="Flowchart of the webhook process. An arrow labeled “HTTP POST” points from an External Application to a Webhook, which has an arrow labeled “Starts runbook” pointing to a Runbook. The Webhook and Runbook are within a square labeled Automation. These three icons are in a larger square labeled Azure."></p>

### Create a webhook
You create a webhook linked to a runbook using the following steps:

1. In the Azure portal, open the runbook that you want to create the webhook for.
2. In the runbook pane, under Resources, select **Webhooks**, and then select **+ Add webhook**. 
3. Select **Create new webhook**. 
4. In the **Create new webhook** dialog, there are several values you need to configure. After you configure them, select **Create**:
    - **Name**. Specify any name you want for a webhook, because the name is not exposed to the client; it's only used for you to identify the runbook in Azure Automation.
    - **Enabled**. A webhook is enabled by default when it is created. If you set it to Disabled, then no client is able to use it.
    - **Expires**. Each webhook has an expiration date at which time it can no longer be used. You can continue to modify the date after creating the webhook providing the webhook is not expired
    - **URL**. The URL of the webhook is the unique address that a client calls with an HTTP POST, to start the runbook linked to the webhook. It is automatically generated when you create the webhook, and you cannot specify a custom URL. The URL contains a security token that allows the runbook to be invoked by a third-party system with no further authentication. For this reason, treat it like a password. For security reasons, you can only view the URL in the Azure portal at the time the webhook is created. Make note of the URL in a secure location for future use.

        <p style="text-align:center;"><img src="../Linked_Image_Files/webhookparameters.png" alt="Diagram representing structure and flow of webhook parameter values and how they flow. The webhook starts with an incoming HTTP POST request. An arrow points to a box containing the webhook (webhook name, request headers, request body), which in turn points to a box containing runbook parameter objects."></p>
    
    > **Note**: Make sure you make a copy of the webhook URL when creating it, and then store it in a safe place. After you create the webhook, you cannot retrieve the URL again.

4. Select the **Parameters run settings (Default : Azure)** option. This option  has the following characteristics, which allows you to complete the following actions:
    - If the runbook has mandatory parameters, you will need to provide these mandatory parameters during creation. You are not able to create the webhook unless values are provided.
    - If there are no mandatory parameters in the runbook, there is no configuration required here.
    - The webhook must include values for any mandatory parameters of the runbook, but could also include values for optional parameters.
    - When a client starts a runbook using a webhook, it cannot override the parameter values defined in the webhook.
    - To receive data from the client, the runbook can accept a single parameter called $*WebhookData* of type `[object]` that contains data that the client includes in the POST request.
    - There is no required webhook configuration to support the *$WebhookData* parameter.

    <p style="text-align:center;"><img src="../Linked_Image_Files/createwebhook1.png" alt="Screenshot of both Create a new webhook panes. A warning explains that after creating a webhook, its URL can’t be viewed, so be sure to copy it before pressing OK. At the bottom of the pane, the URL displays with a copy button next to it."></p>

5. When finished, select **Create**.

### Using a Webhook
To use a webhook after it has been created, your client application must issue an HTTP POST with the URL for the webhook. 

- The syntax of the webhook is in the following format:
    
    ```
       http://< Webhook Server >/token?=< Token Value >
    ```

- The client receives one of the following return codes from the POST request.

    |Code|Test|Description
    |---|---|---|
    |202|Accepted|the request was accepted and the runbook is successfully queued|
    |400|Bad request|The request was not accepted because the runbook has expired, been disabled, or the token in the URL is invalid|
    |404| Not found|The request was not accepted because the webhook, runbook, or account was not found|
    |500|Internal Server Error|
    

- If successful, the webhook response contains the job ID in JSON format as follows:

    ```json
    {"JobIds":["< JobId >"]}
    ```

The response will contain a single job ID, but the JSON format allows for potential future enhancements.

- You cannot determine when the runbook job completes or determine its completion status from the webhook. You can only determine this information using the job ID with another method such as PowerShell or the Azure Automation API.


> **Note**: More details are available on the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-webhooks#details-of-a-webhook" target="_blank"><span style="color: #0066cc;" color="#0066cc">Starting an Azure Automation runbook with a webhook</span></a> page.
