You can run **Ansible** playbooks on a Windows machine by using the Azure Cloud Shell with **Bash**. This is the quickest and easiest way to get up and running with playbooks provisioning and managing in Azure.


### run commands
**Azure Cloud Shell**, has **Ansible** pre-installed. As such, once you are logged into **Azure Cloud Shell**, specify the **bash** console, you do not have to install or configure anything to be able or run **Anbsible**

<p style="text-align:center;"><img src="../Linked_Image_Files/ansibelcloudshell1.png" alt="Hybrid cloud icon"></p>


### Editor
You can also use the editor included with Azure Cloud Shell to view, open and edit your playbook `.yml` files. You can open the editor by clicking on the curly brackets icon in the taskbar at the top of Azure cloud Shell


<p style="text-align:center;"><img src="../Linked_Image_Files/ansibelcloudshelleditor.png" alt="Hybrid cloud icon"></p>

### Create a resource group in Azure using Ansible in Azure Cloud Shell wth bash
The following steps outline how to create a resource group in Azure using Ansible in Azure Cloud Shell wth bash

1. Go to the Azure Cloud Shell at https://shall.azure.com or launch Azure Cloud Shell from within the Azure Portal by clicking on the Azure PowerShell icon in the top left.
2. Authenticate to Azure, entering your credentials if prompted.
3. Ensure **Bash** is selected as the shell, at the top left in the taskbar.

4. Create a new file

    ```yml
    vi rg.yml
    ```

5. Enter **insert** mode by selecting the **I** key.
6. copy and paste the below code into the file.

    ```yml
        ---
        - hosts: localhost
          connection: local
          tasks:
            - name: Create resource group
              azure_rm_resourcegroup:
                name: ansible-rg
                location: eastus
    ```

7. Exit **insert** mode by selecting the **Esc** key.

8. Save the file and exit the **vi** editor by entering the following command:
 
    ```
    :wq
    ```
9. Run the playbook by running the command

    ```yml
    ansible-playbook rg.yml
    ```

10. You should receive output similar to the below

    ```yml
    PLAY [localhost] *********************************************************************************
    
    TASK [Gathering Facts] ***************************************************************************
    ok: [localhost]
    
    TASK [Create resource group] *********************************************************************
    changed: [localhost]
    
    TASK [debug] *************************************************************************************
    ok: [localhost] => {
        "rg": {
            "changed": true,
            "contains_resources": false,
            "failed": false,
            "state": {
                "id": "/subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/ansible-rg",
                "location": "eastus",
                "name": "ansible-rg",
                "provisioning_state": "Succeeded",
                "tags": null
            }
        }
    }
    
    PLAY RECAP ***************************************************************************************
    localhost                  : ok=3    changed=1    unreachable=0    failed=0
    ```

11. Open Azure portal and verify the resource group is now present in the portal.