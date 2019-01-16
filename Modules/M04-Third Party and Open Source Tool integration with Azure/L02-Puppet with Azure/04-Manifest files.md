Puppet uses a declarative file syntax to define state. In other words, it defines *what* the infrastructure state should be, but not *how* it should be achieved. You tell it you want to install a package, not how you want to install the package.

### Manifest files

With Puppet, *Configuration*, or *State*, is defined in manifest files known as *Puppet Program* files. These files have the file extension `.pp`. The Puppet Program are used to determine the state of an application.

Puppet Program files include the following elements:

- *Class* define related resources according to their classification. For example, we might have an `Apache` class for all the things required to run `Apache`, i.e. the package, the config file, the running server, and any users that need to be created. That class then acts as an entity that we can ship around and reuse to compose other workflows.

- *Resource* is a single element of your configuration which you can specify parameters for, such as a user, a package, a file, etc.

- *Module* is the collection of all the classes, resources and other elements of the Puppet program file in a single entity.

> :information_source: The main elements of a Puppet Program (PP) Manifest file are Class, Resource and Module.

### Sample Manifest file

The following is a sample `.pp` file.

We can see the classes defined, and within that, resources and package details.

The `->` notation is an 'ordering arrow': it tells Puppet that it must apply the 'left' resource before invoking the 'right' resource. This allows us to specify order, when necessary.

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

> :information_source: You can download modules for Puppet that have been created by Puppet and the Puppet community from [Puppetforge](https://forge.puppet.com/).
>
> Puppetforge is a community repository that contains lots of modules for download, reuse and modification. Reusing modules can save you coding and testing time.
