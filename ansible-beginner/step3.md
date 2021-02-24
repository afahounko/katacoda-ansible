## The Ansible configuration files

The behavior of Ansible can be customized by modifying settings in Ansible’s ini-style configuration file. Ansible will select its configuration file from one of several possible locations on the control node, please refer to the documentation.

TIP: The recommended practice is to create an ansible.cfg file in a directory from which you run Ansible commands. This directory would also contain any files used by your Ansible project, such as the inventory and playbooks.

Make sure your inventory file is used by default when executing commands from the `inventory` directory:

```
cat << EOF > ansible.cfg
[defaults]
inventory=${PWD}/inventory
EOF
```{{execute}}


Check the content of the config file `learn-ansible/ansible.cfg`{{open}}


On control.cloud.ws.afnog.org 1 as ansible create the file ~/ansible-files/ansible.cfg with the following content:
[defaults]
inventory=/home/ansible/ansible-files/inventory
Check with ansible --version, first from ansible’s home directory and then from ~/ansible-files/. You’ll notice on the second line of the output that, when run from ~/ansible-files/, your personal config settings override the settings from the main config file.
From ~/ansible-files/ run ansible all --list-hosts.
Your Ansible inventory was used without providing the -i option. To double-check, run the command again from outside ~/ansible-files/:

[ansible@control-6656 ~]$ ansible all --list-hosts
 
 [WARNING]: provided hosts list is empty, only localhost is available. Note that
the implicit localhost does not match 'all'

  hosts (0):
