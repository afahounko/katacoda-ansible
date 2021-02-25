## The Ansible configuration files

The behavior of Ansible can be customized by modifying settings in Ansible’s ini-style configuration file. Ansible will select its configuration file from one of several possible locations on the control node, please refer to the documentation.

TIP: The recommended practice is to create an ansible.cfg file in a directory from which you run Ansible commands. This directory would also contain any files used by your Ansible project, such as the inventory and playbooks.

Make sure your inventory file is used by default when executing commands from the `inventory` directory:

```
cat << EOF > ansible.cfg
[defaults]
inventory=${PWD}/inventory
EOF
```{{execute T2}}


Check the content of the config file `learn-ansible/ansible.cfg`{{open}}

Run again the version of `ansible` and check the path of the config file in use

`ansible --version`{{execute T2}}

Run all the previous commands without specifying the inventory file

`ping` command:

`ansible all -m ping`{{execute T2}}

`setup` for the controller node `facts`:

`ansible controller_node -m setup`{{execute T2}}

