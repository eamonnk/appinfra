You can run Ansible playbooks on a Windows machine by using the Azure Cloud Shell with Bash. This is the quickest and easiest way to begin using playbook's provisioning and managing in Azure.


### Run commands
Azure Cloud Shell, has Ansible preinstalled. After you are signed into Azure Cloud Shell, specify the bash console. (You do not have to install or configure anything to be able or run Ansible.)

<p style="text-align:center;"><img src="../Linked_Image_Files/ansibelcloudshell1.png" alt="Screenshot of Bash running in Azure Cloud Shell."></p>


### Editor
You can also use the editor included with Azure Cloud Shell to view, open, and edit your playbook .yml files. You can open the editor by clicking on the curly brackets icon in the taskbar at the top of Azure Cloud Shell.


<p style="text-align:center;"><img src="../Linked_Image_Files/ansibelcloudshelleditor.png" alt="Screenshot of the Azure Editor running in Azure Cloud Shell."></p>

### Create a resource group

The following steps outline how to create a resource group in Azure using Ansible in Azure Cloud Shell with bash:

 
1. Go to the Azure Cloud Shell at <a href="https://shell.azure.com"><span style="color: #0066cc;" color="#0066cc">https://shell.azure.com</span></a>, or launch Azure Cloud Shell from within the Azure portal by clicking on the Azure PowerShell icon in the taskbar's top, left corner.
2. Authenticate to Azure by entering your credentials if prompted.
3. Ensure **Bash** is selected as the shell, in the taskbar's top, left corner.

4. Create a new file using the following command:

    ```yml
    vi rg.yml
    ```

5. Enter insert mode by selecting the **I** key.
6. Copy and paste the following code into the file, and remove the comment character, #, it is included here ot allow it display properly in the learning platform. The code should look like and be aligned as it is in the earlier screenshot.

    ```yml
       #---
        - hosts: localhost
          connection: local
          tasks:
            - name: Create resource group
              azure_rm_resourcegroup:
                name: ansible-rg
                location: eastus
    ```

7. Exit insert mode by selecting the **Esc** key.

8. Save the file and exit the **vi** editor by entering the following command:
 
    ```
    :wq
    ```
9. Run the playbook by running the following command:

    ```yml
    ansible-playbook rg.yml
    ```

10. Verify that you receive output similar to the following code:

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

11. Open Azure portal and verify the resource group now displays in the portal.