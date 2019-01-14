

**Chef** uses a *cookbook* to define a set of commands that you want to execute on your managed client. 

A *cookbook* is a set of tasks for configuring an application or feature. It defines a scenario and everything required to support that scenario. Within a cookbook, there are a series of *recipes* that define a set of actions to perform. Cookbooks and recipes are written in the Ruby language.

Once a cookbook is created you cna then create a *Role* to define a baseline set of cookbooks and attributes that can be applied to multiple servers.


To create a Cookbook you use the **chef generate cookbook** command.


### Creating cookbooks
Before creating a cookbook, you should first configure your Chef Workstation by setting up the Chef Development Kit on your local workstation. It is from the Chef workstation that you will connect to and manage your Chef server.

1. You can download and install the Chef Development Kit from <a href="https://downloads.chef.io/chefdk" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://downloads.chef.io/chefdkt</span></a> https://downloads.chef.io/chefdk, choosing the appropriate version for your environment, i.e. Mac OSX/macOS, Debian, Red Hat Enterprise Linux SUSE LInux Enterprise Server,Ubuntu, Windows and choosing the correct flavour within those groupings.

2. Once installed under your **C:\Chef** directory, 9which is created during installation of thr ChefDK, run the below command. this example calls the Cookbook web server for a policy that automatically deploys IIS.

```ruby
chef generate cookbook webserver
```

This will generate a set of files under the directory **C:\Chef\cookbooks\webserver**. Next, you need to define the set of commands that you would like the Chef client to execute on your managed virtual machine.

3. The commands are stored in the file **default.rb**. For this example, a set of commands will be defined that installs IIS, starts IIS, and copies a template file to the wwwroot folder. Modify the **C:\chef\cookbooks\webserver\recipes\default.rb** file and add the following lines:

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

6. Upload the cookbook to the Chef Server so that it appears under the **Policy** tab by running the following command:

```ruby
chef generate template webserver Default.htm
```
We have now created our cookbook for use. We will not outline the next steps here but the next steps would be to:
- Create a Role to define a baseline set of cookbooks and attributes that can be applied to multiple servers.
- Create a node to deploy the configuration to i.e. the machine yuo wish to configure.
- Bootstrap the  machine to add the role to the node i.e. deployed the configuration to the machine using Chef.
