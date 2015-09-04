Nagios NRPE Server Config
=========

[![GitHub version](https://badge.fury.io/gh/Mooash%2Fnagios-nrpe-server.svg)](http://badge.fury.io/gh/Mooash%2Fnagios-nrpe-server) [![Build Status](https://travis-ci.org/Mooash/nagios-nrpe-server.svg?branch=master)](https://travis-ci.org/Mooash/nagios-nrpe-server)

[![Join the chat at https://gitter.im/Mooash/project-chat](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Mooash/project-chat?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

An Ansible role to handle the installation and rollout of the Nagios NRPE Daemon.

I've only selected certain platforms that I know this 100% works on, but it should work on any platform that NRPE can be installed on.

Currently supports:

 * Debian
   - Squeeze
   - Wheezy
 * Ubuntu
   - Raring
   - Saucy
   - Trusty
 * RedHat
   - At least 6 onwards
 * Arch Linux
   - All
 * Solaris
   - At least 11.1

Requirements
------------

RedHat based OS's must have the EPEL repo.

Role Information
--------------

This role gives you the ability to deploy plugins on a global and per-server basis. This can be done by putting plugins into [`files/plugins/global`](files/plugins/global) or by creating a folder in `files/plugins/` that is the servers [FQDN](http://en.wikipedia.org/wiki/Fully_qualified_domain_name).

You can find out your servers FQDN by running the [Ansible Setup](http://docs.ansible.com/setup_module.html) module.

Role Variables
--------------

  * *nagios_nrpe_server_bind_address*: 127.0.0.1
  * *nagios_nrpe_server_port*: 5666
  * *nagios_nrpe_server_allowed_hosts*: 127.0.0.1

These are OS specific and likely wont want to be changed

Debian:

  * *nagios_nrpe_server_pid*: /var/run/nagios/nrpe.pid
  * *nagios_nrpe_server_user*: nagios
  * *nagios_nrpe_server_group*: nagios
  * *nagios_nrpe_server_service*: nagios-nrpe-server
  * *nagios_nrpe_server_plugins_dir*: /usr/lib/nagios/plugins
  * *nagios_nrpe_server_dir*: /etc/nagios

RedHat:

  * *nagios_nrpe_server_pid*: /var/run/nrpe/nrpe.pid
  * *nagios_nrpe_server_user*: nrpe
  * *nagios_nrpe_server_group*: nrpe
  * *nagios_nrpe_server_repo_redhat*: epel
  * *nagios_nrpe_server_service*: nrpe
  * *nagios_nrpe_server_dir*: /etc/nagios

Arhc Linux:
  * *nagios_nrpe_server_pid*: /var/run/nrpe/nrpe.pid
  * *nagios_nrpe_server_user*: 31
  * *nagios_nrpe_server_group*: 31
  * *nagios_nrpe_server_service*: nrpe
  * *nagios_nrpe_server_plugins_dir*: /usr/lib/monitoring-plugins
  * *nagios_nrpe_server_dir*: /etc/nrpe

Solaris:
  * *nagios_nrpe_server_dir*: /etc/opt/csw
  * *nagios_nrpe_server_group*: nagios
  * *nagios_nrpe_server_pid*: /var/run/nrpe.pid
  * *nagios_nrpe_server_plugins_dir*: /opt/csw/libexec/nagios-plugins
  * *nagios_nrpe_server_service*: svc:/network/cswnrpe:default
  * *nagios_nrpe_server_user*: nagios

Dependencies
------------

N/A

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - mooash.nagios-nrpe-server
   vars:
     nagios_nrpe_server_allowed_hosts: 192.168.0.1,127.0.0.1
```

License
-------

MIT

Author Information
------------------

Checkout my blog [here](http://www.mooash.me)
