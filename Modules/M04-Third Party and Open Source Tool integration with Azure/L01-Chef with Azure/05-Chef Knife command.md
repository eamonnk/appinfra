

*Knife* is a command that's available from the command line. It's made available as part of the Chef Development Kit installation. You can use the **Knife** command to complete a wide variety of tasks, such as:

- Generate a cookbook template. You do this by running the following command:

    ```ruby
    chef generate cookbook < cookbook name >
    ```

- Upload your cookbooks and recipes to the Chef Automate server using the following command:

    ```ruby
    knife cookbook upload < cookbook name> --include-dependencies
    ```

- Create a role to define a baseline set of cookbooks and attributes that you can apply to multiple servers. Use the following command to create this role:

    ```ruby
    knife role create < role name >
    ```

- Bootstrap the a node or client and assign a role using the following command:

    ```ruby
     knife bootstrap < FQDN-for-App-VM > --ssh-user <app-admin-username> --ssh-password <app-vm-admin-password> --node-name  < node name > --run-list role[ < role you defined > ] --sudo --verbose
    ```

You can also bootstrap Chef VM extensions for the Windows and Linux operating systems, in addition to provisioning them in Azure using the **Knife** command. For more information, look up the ‘cloud-api’ bootstrap option in the Knife plugin documentation at <a href="https://github.com/chef/knife-azure" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/chef/knife-azure</span></a>.

> **Note**: You can also install the Chef extensions to an Azure VM using Windows PowerShell. By installing the Chef Management Console, you can manage your Chef server configuration and node deployments via a browser window.
