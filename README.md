Nagios NRPE Server Config
=========

A Ansible role to handle the installation and rollout of the Nagios NRPE Daemon.

I've only selected certain platforms that I know this 100% works on, but it will work on any platform that NRPE can be installed on.

Requirements
------------

RedHat based OS's must have the EPEL repo.

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

RedHat:

  * *nagios_nrpe_server_pid*: /var/run/nrpe/nrpe.pid
  * *nagios_nrpe_server_user*: nrpe
  * *nagios_nrpe_server_group*: nrpe
  * *nagios_nrpe_server_repo_redhat*: epel
  * *nagios_nrpe_server_service*: nrpe


Dependencies
------------

N/A

Example Playbook
----------------

    - hosts: servers
      roles:
         - mooash.nagios-nrpe-server
       vars:
         nagios_nrpe_server_allowed_hosts: 192.168.0.1,127.0.0.1

License
-------

MIT

Author Information
------------------

Checkout my blog [here](http://www.mooash.me)
