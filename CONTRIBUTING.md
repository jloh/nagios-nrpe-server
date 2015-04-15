### General

I've set some general contribution outlines [here](https://mooash.github.io/contributing/#pk_campaign=GitHub-Project&pk_kwd=nagios-nrpe-server). Please read them before opening a pull request.

### Project Specific

#### Ansible formatting

I try and follow Ansible's [playbook best practices](https://docs.ansible.com/playbooks_best_practices.html) to the best of my ability. That said, these rules always apply:

 * [Always Mention The State](https://docs.ansible.com/playbooks_best_practices.html#always-mention-the-state)
 * Move big plays to multiple lines. Plays like template look ugly on single lines.  
   Not OK:

   ```yaml
   # Create nrpe_ansible.cfg
    - name: Create nrpe_ansible.cfg from template
      sudo: true
      template: src="nrpe_ansible.cfg.j2" dest="{{ nagios_nrpe_server_dir }}/nrpe_ansible.cfg" owner=root group=root mode=0644
      notify: restart nagios-nrpe-server
    ```

    OK:

    ```yaml
    # Create nrpe_ansible.cfg
    - name: Create nrpe_ansible.cfg from template
      sudo: true
      template: >
        src="nrpe_ansible.cfg.j2"
        dest="{{ nagios_nrpe_server_dir }}/nrpe_ansible.cfg"
        owner=root group=root mode=0644
      notify: restart nagios-nrpe-server
    ```
 * If a play is OS specific, state it in the play name.  
   eg: `- name: Installing packages [Debian]` or `- name: Installing packages [RedHat]`

### Questions?

If you're confused on any of the above, just contact me so I can clear up my documentation.
