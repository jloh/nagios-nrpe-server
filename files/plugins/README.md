Place plugin files here so that they're deployed by Ansible.

Files in the `files/plugins/global/` folder will be deployed to all systems, files in `files/plugins/{{ ansible_fqdn }}/` will only be deployed to the server that has that FQDN.
