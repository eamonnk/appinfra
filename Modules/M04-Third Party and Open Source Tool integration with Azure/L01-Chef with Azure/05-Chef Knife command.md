

**Knife** is a command available from the command line, made available as part of the *Chef Development Kit installation* that  you can use to complete a wide variety of tasks, such as:


- Use the **knife** tool to generate a cookbook template by running the following command

```ruby
chef generate cookbook < cookbook name >

```

- The **Knife** command can upload our cookbooks and recipes to the Chef Automate server with the command

```
knife cookbook upload < cookbook name> --include-dependencies

```

- Use the knife command to create a role to define a baseline set of cookbooks and attributes that can be applied to multiple servers.

```ruby
knife role create < role name >
````

- run the knife command to bootstrap the MRP app server and assign the MRP application role 

```ruby
 knife bootstrap < FQDN-for-App-VM > --ssh-user <app-admin-username> --ssh-password <mrp-app-admin-password> --node-name  < node name > --run-list role[ < role you defined > ] --sudo --verbose

```

It is also possible to bootstrap Chef VM Extensions for windows and Linux in addition to provisioning Virtual machines in Azure using **Knife**. Lookup the ‘cloud-api’ bootstrap option in the Knife plugin documentation on the <a href="https://github.com/chef/knife-azure" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/chef/knife-azure</span></a> page.

> **Note**: It is also possible to install the Chefextension to an azure virtual machine using PowerShell.

> **Note**: You can also manage your Chef server configuration and node deployments, via a browser by installing the Chef Management Console. 
