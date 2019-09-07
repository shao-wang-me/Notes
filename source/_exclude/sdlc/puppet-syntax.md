# Puppet Syntax

## Resource definition
package { 'ntp':
  ensure => installed
}
service { 'ntp':
  name => $service_name,
  ensure => running,
  enable => true,
  subscribe => File['ntp.conf'] ## reference another resource
}
file { 'ntp.conf':
  path => '/etc/ntp.conf',
  ensure => file,
  require => Package['ntp'],
  source => "puppet:///modules/ntp/ntp.conf"
}

## Variable declaration and assignment
$package_list = ['ntp', 'apache2', 'vim-nox', 'wget'] ## list
$myhash = { key => { subkey => 'b' }} ## puppet call this hash, but shouldn't it be dictionary?

## Class definition
class ntp {
  package {'ntp':
    ...
  }
  ...
}
class ntp

## Class declaration, well it's actually just using the class, three ways:
include ntp
require ntp
class {'ntp':}
class {'ntp': servers => ['nist-time-server.eoni.com','nist1-lv.ustiming.org','ntp-nist.ldsbc.edu']} ## with parameters?

## Node definition
node 'www1.example.com' {
  include common
  include apache
  include squid
}
node /^www\d+$/ {
  include common
}

## Comment
/* Comment */

## If-elsif-else
if $is_virtual {
  warning( 'Tried to include class ntp on virtual machine; this node might be misclassified.' )
}
elsif $operatingsystem == 'Darwin' {
  warning( 'This NTP module does not yet work on our Mac laptops.' )
else {
  include ntp
}
if $hostname =~ /^www(\d+)\./ {
  notify { "Welcome web server ##$1": }
}
if 'www' in $hostname {
  ...
}

## Case
case $operatingsystem {
  'Solaris':          { include role::solaris }
  'RedHat', 'CentOS': { include role::redhat  }
  /^(Debian|Ubuntu)$/:{ include role::debian  }
  default:            { include role::generic }
}

## Conditional value
$rootgroup = $osfamily ? {
    'Solaris'          => 'wheel',
    /(Darwin|FreeBSD)/ => 'wheel',
    default            => 'root',
}

/* Puppet Core Resource Types
These resource types are in Puppet by default (in puppet-server and puppet-agent):
1. exec: Executes external command.
2. file
3. filebucket: A file repository. "All puppet masters provide a filebucket service that agent nodes can access via HTTP".
4. group: OS user group.
5. notify: Log something in the agent's log.
6. package:
7. resources: Metatype to manage other resources.
8. schedule: Define a schedule and then in another resource, by using `schedule` metaparameter, you can indicate the schedule to use. Currently, schedules can only be used to stop a resource from being applied.
9. service: 
10. tidy: Remove files. It is actually just a wrapper of `file` resource type.
11. user
These additional resource types are in Puppet Agent by default (only available in puppet-agent):
1. augeas
2. cron
3. host
4. mount
5. scheduled_task
6. selboolean
7. selmodule
8. ssh_authorized_key
9. sshkey
10. yumrepo
11. zfs
12. zone
13. zpool
*/

