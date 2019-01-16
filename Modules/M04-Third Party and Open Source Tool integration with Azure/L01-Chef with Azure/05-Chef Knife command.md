With Chef, the `knife` command is a available from the command line. The Chef Development Kit contains the `knife` command, and you can use the command to for a variety of tasks.  The following describes some command line uses for Chef and the `knife` command.

- Use the Chef to generate a cookbook template by running the following command.

  ```ruby
    chef generate cookbook < cookbook name >
  ```

- The following shows how to use the `knife` command to upload a cookbook to the Chef Automate server.

  ```ruby
    knife cookbook upload < cookbook name> --include-dependencies

  ```

- Use `knife` to create a role by running the following command. Roles can define a baseline set of cookbooks and attributes that can be applied to multiple servers.

  ```ruby
    knife role create < role name >
  ```

- Running the following the `knife` command bootstraps the MRP app server and assigning the MRP application role.

  ```ruby
    knife bootstrap < FQDN-for-App-VM > --ssh-user <app-admin-username> --ssh-password <mrp-app-admin-password> --node-name  < node name > --run-list role[ < role you defined > ] --sudo --verbose
  ```

>:information_source: In addition to provisioning virtual machines in Azure using `knife`, it is possible to bootstrap Chef VM Extensions for Windows and Linux. For more information see the `cloud-api` bootstrap option in the [Knife plugin documentation](https://github.com/chef/knife-azure).
>
> It is also possible to install the `Chefextension` to an azure virtual machine using PowerShell.
>
> You can even manage your Chef server configuration and node deployments, via a browser by installing the *Chef Management Console*.
>
> For more information about using Chef with Azure virtual machines see the page [Automating Azure virtual machine deployment with Chef](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/chef-automation).
