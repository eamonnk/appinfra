Chef uses a *cookbook* to define a set of commands that you want to execute on your managed client.

A cookbook is a set of tasks for configuring an application or feature. It defines a scenario and everything required to support that scenario. Within a cookbook, there are a series of *recipes* that define a set of actions to perform. Cookbooks and recipes are written in the Ruby language.

You can assign a *role* to cookbooks. Roles define a baseline set of cookbooks and attributes that can be applied to multiple servers.

### Creating cookbooks

Cookbooks are created with the `chef generate cookbook` command.

Before creating a cookbook, you should first configure your Chef Workstation by setting up the *Chef Development Kit* on your local workstation. You connect to and manage your Chef server from the Chef Workstation.

1. Download and install the [Chef Development Kit](https://downloads.chef.io/chefdk). Be sure to choose the version of the Chef Development Kit appropriate to your environment's operating system. It is important that you select the correct version, i.e. Linux Debian, Red Hat Enterprise Linux, macOS, SUSE Linux Enterprise Server, Ubuntu or Windows. The following steps use the Chef Development Kit for Windows.

2. Chef is installed under the `C:\Chef` directory. This directory is created during installation of the Chef Development Kit (Chefdk). In the following example, running the command `chef generate cookbook webserver` calls the Cookbook Web Server for a policy that automatically deploys IIS. This will generate a set of files under the directory `C:\Chef\cookbooks\webserver`.

  ```ruby
    chef generate cookbook webserver
  ```

3. Next, you will define a set of commands for the Chef client to execute on a managed virtual machine. The commands will be stored in the file `default.rb`. For this example, the set of commands you define install IIS, start IIS, and copy a template file to the `wwwroot` directory.

    Modify the file `C:\chef\cookbooks\webserver\recipes\default.rb` by adding the following lines:

  ```ruby
    powershell_script 'Install IIS' do

    action :run

    code 'add-windowsfeature Web-Server'

    end

    service 'w3svc' do

    action [ :enable, :start ]

    end

    template 'c:\inetpub\wwwroot\Default.htm' do

    source 'Default.htm.erb'

    rights :read, 'Everyone'

    end
  ```

3. Now, save the file.

4. To generate the template, run the following command:

  ```ruby
    chef generate template webserver Default.htm
  ```

5. Now, navigate to the file `C:\chef\cookbooks\webserver\templates\default\Default.htm.erb`. Edit the file by adding some simple *Hello World* HTML code, and then save the file.

6. Upload the cookbook to the Chef Server so that it appears under the **Policy** tab by running the following command:

  ```ruby
    chef generate template webserver Default.htm
  ```

You have created your first cookbook for use.

### Using cookbooks

Providing a detailed account of the next steps that are required to use cookbook are beyond the scope of this lesson. However, the following is a brief overview of the steps you would need to take to use the cookbook.

- Create a *Role* to define a baseline set of cookbooks and attributes to be applied to multiple servers.
- Create a *Node* to deploy the configuration to, i.e. the machine you want to configure.
- Bootstrap the machine to add the role to the node, i.e. deploy the configuration to the machine using Chef.
