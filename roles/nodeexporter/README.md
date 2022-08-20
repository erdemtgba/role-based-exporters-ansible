# Node Exporter Installation with Ansible

This project helps us about if we have more than one host for same installation. We can install node exporter with just one ansible-playbook command to all our hosts.

## Prerequisites

- ansible-cli for your local terminal (more info <https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html>)
- Any editor tool like VS Code for edit playbook.yml

Let's start. There are four milestones of installation with ansible. These are 
1. hosts file
2. playbook.yml
3. main.yml
4. templates

## Hosts

```
[all:vars]
ansible_connection= ssh
#ubuntu is my ssh user
ansible_user=ubuntu
# pem file path for ssh 
ansible_ssh_private_key_file=pem-file-path/my-pem-file.pem

[servers]
# x.x.x.x  --server ip addresses 1
# x.x.x.x  --server ip addresses 2
```

After the hosts configuring, We can configure playbook.yml with our references.

```
- hosts: servers
  become: yes
  gather_facts: true
  roles:
    - nodeexporter
```

