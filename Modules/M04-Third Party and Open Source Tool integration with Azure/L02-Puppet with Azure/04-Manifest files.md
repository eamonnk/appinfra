
Puppet uses a declarative file syntax to define state. It defines what the infrastructure state should be but not how it should be achieved, so you tell it you want to install a package, not how you want to install the package. 


### Manifest files
Configuration, or State, is defined in manifest files known as **Puppet Program** file. These files have the file extension `.pp`. It is these configuration files that determine the state of the application.  Puppet program files have element which include:

- **class** -  a bucket to allow you put resources into. For example, we might have an *Apache* class with all the things required to run *Apache*, i.e. the package, the config file the running server and any users that need ot be created. That class then becomes an entity that we can ship around an use to compose other workflows.

- resources - single elements of your configuration which you cna specify parameters for.



A **Module** is the collection of all the classes, resources and other elements of the Puppet program file into a single entity.



### Sample Manifest file
The following is a sample .pp file.

We can see the classes being defined, and within that, resources and package details.

The -> notation is an “ordering arrow”: it tells Puppet that it must apply the “left” resource before invoking the “right” resource. This allows us to specify order when necessary

```ruby

class mrpapp {
  class { 'configuremongodb': }
  class { 'configurejava': }
}

class configuremongodb {
  include wget
  class { 'mongodb': }->

  wget::fetch { 'mongorecords':
    source => 'https://raw.githubusercontent.com/Microsoft/PartsUnlimitedMRP/master/deploy/MongoRecords.js',
    destination => '/tmp/MongoRecords.js',
    timeout => 0,
  }->
  exec { 'insertrecords':
    command => 'mongo ordering /tmp/MongoRecords.js',
    path => '/usr/bin:/usr/sbin',
    unless => 'test -f /tmp/initcomplete'
  }->
  file { '/tmp/initcomplete':
    ensure => 'present',
  }
}

class configurejava {
  include apt
  $packages = ['openjdk-8-jdk', 'openjdk-8-jre']
  apt::ppa { 'ppa:openjdk-r/ppa': }->
  package { $packages:
     ensure => 'installed',

 }
}
```



> **Note**: You can download customer Puppet modules that have been created by Puppet and the Puppet community on <a href="https://forge.puppet.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://forge.puppet.com/</span></a>. **Puppetforge** is a community repository that contains 1000s of modules that you can download and use or modify as you need, so you do not have to create modules from scratch yourself.