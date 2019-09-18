

Chef uses a cookbook to define a set of commands that you execute on your managed client. A *cookbook* is a set of tasks that you use to configure an application or feature. It defines a scenario and everything required to support that scenario. Within a cookbook, there are a series of *recipes*, which define a set of actions to perform. Cookbooks and recipes are written in the Ruby language.

After you create a cookbook, you can then create a  Role. A *Role* defines a baseline set of cookbooks and attributes that you can apply to multiple servers. To create a cookbook, you use the **chef generate cookbook** command.


### Creating a cookbook
Before creating a cookbook, you first configure your Chef Workstation by setting up the Chef Development Kit on your local workstation. You'll use the Chef workstation to connect to and manage your Chef server.

> **Note**: You can download and install the Chef Development Kit from <a href="https://downloads.chef.io/chefdk" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://downloads.chef.io/chefdkt</span></a>.
>
> Choose the Chef Development Kit that is appropriate to your operating system and version. For example:
> - macOSX/macOS
> - Debian
> - Red Hat Enterprise Linux SUSE
> - Linux Enterprise Server
> - Ubuntu
> - Windows



1. Installing the Chef Development Kit creates the Chef workstation automatically in your **C:\Chef** directory. After installation completes, run the following example command that calls the Cookbook web server for a policy that automatically deploys IIS:

    ```ruby
    chef generate cookbook webserver
    ```

    This command generates a set of files under the directory **C:\Chef\cookbooks\webserver**. Next, you need to define the set of commands that you want the Chef client to execute on your managed virtual machine. The commands are stored in the **default.rb** file. 

2. For this example, a set of commands will be defined that installs and starts Microsoft Internet Information Services (IIS), and copies a template file to the **wwwroot** folder. Modify the **C:\chef\cookbooks\webserver\recipes\default.rb** file by adding the following lines:

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

3. Save the file after you are done.

4. To generate the template, run the following command:

    ```ruby
    chef generate template webserver Default.htm
    ```

5. Now navigate to the **C:\chef\cookbooks\webserver\templates\default\Default.htm.erb** file. Edit the file by adding some simple **Hello World** HTML code, and then save the file. 

6. Run the following command to upload the cookbook to the Chef Server so that it appears under the **Policy** tab:

    ```ruby
    chef generate template webserver Default.htm
    ```

We have now created our cookbook and it's ready to use. 

The next steps (which we will not be covering at this time), would be to:

1. Create a role to define a baseline set of cookbooks and attributes that you can apply to multiple servers.
2. Create a node to deploy the configuration to the machine you want to configure.
3. Bootstrap the machine using Chef to add the role to the node that deployed the configuration to the machine.
