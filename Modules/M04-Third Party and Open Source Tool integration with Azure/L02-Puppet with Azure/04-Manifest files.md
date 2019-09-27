
Puppet uses a declarative file syntax to define state. It defines what the infrastructure state should be, but not how it should be achieved. You must tell it you want to install a package, but not how you want to install the package.

### Manifest files

Configuration or state, is defined in manifest files known as *Puppet Program files*. These files are responsible for determining the state of the application, and have the file extension **.pp**.

Puppet program files have the following elements:

- **class**. A bucket that you put resources into. For example, you might have an **Apache** class with everything required to run Apache (such as the package, config file. running server, and any users that need to be created). That class then becomes an entity that you can use to compose other workflows.
- **resources**. There are single elements of your configuration that you can specify parameters for.
- **module**. The collection of all the classes, resources, and other elements of the Puppet program file in a single entity.

### Sample manifest (.pp) file

In the following sample .pp file, notice where classes are being defined, and within that, resources and package details are defined.

> **Note**: The -> notation is an “ordering arrow”: it tells Puppet that it must apply the “left” resource before invoking the “right” resource. This allows us to specify order, when necessary.

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

> **Note**: You can download customer Puppet modules that have been created by Puppet and the Puppet community from  <a href="https://forge.puppet.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://forge.puppet.com/</span></a>.
> *Puppetforge* is a community repository that contains thousands of modules for download and use, or modification as you need. This saves you the time necessary to recreate modules from scratch.
