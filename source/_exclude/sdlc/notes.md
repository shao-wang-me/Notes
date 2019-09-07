Puppet
===========

```
C:\PROGRAMDATA\PUPPETLABS\CODE
├───environments
│   └───production
│       │   environment.conf            Configurations for this environment, override puppet.conf
│       │   hiera.yaml                  Hiera file for this env: hierarchy for a given layer of data.
│       │   
│       ├───data                        Data for this environment (production)
│       ├───manifests                   All Puppet source code you write
│       │       site.pp                 Define nodes
│       │       
│       └───modules                     Modules installed by `puppet module install`
│           ├───ntp   
│           ├───stdlib      
│           └───windows_env
│                                   
├───hieradata                           Well, Hieradata?
└───modules                             Like Python's main packages not in virtual env. Global modules
```

# Environment
An environment is an isolated group of agent nodes that a master can serve with its own main manifest and set of modules. It is like a project with its own virtual env in Python with its own packages (modules) and source files (manifests).
## Environment from Git branch
In Puppet documents, another description is "an environment is a branch that gets turned into a directory on your master". For example, in the git repository for Puppet code, you have a master branch for production and a branch created from master for development of the Puppet code, you might would like to try the new branch on a small set of machines. So you get that branch in an environment (e.g. 'develop') instead of the original branch (e.g. 'master'）so the 'master' and 'develop' environments are not affecting each other. Like a virtual env for Python.
## Add nodes to environments
1. In agent's puppet.conf, `environment = production/test`
2. Or use an external node classifier (ENC, just an external script or program that returns a YAML file to classify a node), which will override the setting in puppet.conf

# Hiera
Hiera is used as key-value data source of manifests. It has three layers: global, environment and module. But it's not low level data overriding high level data but the opposite, search in the following order and will terminate once found: global -> environment -> module.

# Manifest
If you specify a manifest directory instead of a single manifest file, it will check the directory tree in depth-first order and items (files/subdirectories) in the same directory in alphabetical order.
One manifest directory is seen as a single manifest file (in the same scope).

# Config version script
You can have a script to generate the version of each catalog (like a compliation or deployment)

# Module
Like a library for Puppet code. To manage modules on your machine, there are three ways:
1. Use `module install` to directly install modules on that machine.
2. r10k
3. Code Manager

# Template
Puppet or Ruby template files, just fill variables. To use:
Embedded Ruby (ERB): `template('my_module/component.erb')`
Embedded Puppet (EPP): `epp('my_module/component.epp')`

# Plug-in
"A plug-in is a custom type, function, or fact that extends Puppet's capabilities and is distributed in a module."
1. Custom facts: written in Ruby for Facter to get more extra facts
2. External facts: non Ruby
3. Puppet functions: return values
4. Ruby functions: functions in Ruby
5. Resource types: new resource types
6. Resource providers: new resource providers
7. Augeas lenses: a way to modify config files

# Puppet Sever
1. `puppetserver` performs the role of the master node. It is written in Ruby and Clojure. Clojure is a functional language running on JVM. Ruby's most popular interpreter is in C but `puppetsever` uses JRuby which runs on JVM as well. So `puppetserver` runs on JVM!
2. `puppetserver` has packages only for Red Hat Enterprise Linux, RHEL-derived distros, Fedora, Debian, and Ubuntu. Although I think it's possible to run on Windows if build from source but service handling would be a problem.
3. Because it uses JRuby packed in itself, `gem` won't work, use `puppetserver gem` instead.
4. Performance can be maximized by tuning JRuby.

# Manage systems with Puppet agent
In a standard Puppet configuration, each node periodically does configuration runs to revert unwanted changes and to pick up recent updates.
On \*nix nodes, there are three main ways to do this:
1. Run Puppet agent as a **service**.
The easiest method. The Puppet agent daemon does configuration runs at a set interval, which can be configured.
2. Make a **cron** job that runs Puppet agent.
Requires more manual configuration, but a good choice if you want to reduce the number of persistent processes on your systems.
3. Only run Puppet agent on demand.
You can also deploy **MCollective** to run on demand on many nodes. Mcollective will be deprecated, there are other ways:
  1. ssh (single machine)
  2. Bolt (multiple machines)
  3. PuppetDB's Puppet Query Language

# Cons
1. Puppet doc is not well organised, easy concepts made complex
2. Puppet is slow, `puppet help` takes 10 seconds, `puppet config print` takes 6 seconds, `puppet module list` takes 7 seconds
3. Puppet is easy but complex. Developers might need some basic introductions
4. (Puppet designers are not good at algorithms)

# Comparisons to other CM tools
1. Vs Ansible: https://www.devopsgroup.com/2018/01/10/puppet-vs-ansible/

# 中文文章
1. 从入门到精通Puppet的实践之路: https://www.cnblogs.com/yuxc/p/3836711.html