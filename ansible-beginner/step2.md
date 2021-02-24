Getting Started with Ansible

## The Inventory
To use the ansible command for host management, you need to provide an inventory file which defines a list of hosts to be managed from the control node. One way to do this is to specify the path to the inventory file with the `-i` option to the ansible command.


Create a directory for your Ansible inventory:

`mkdir  inventory`{{execute}}

Now create a simple inventory file as inventory/hosts with the following content:

```
cat << EOF > inventory/hosts
[runner]
controller_node ansible_connection=local
EOF
```{{execute}}

Check the content of the inventory file `~/learn-ansible/inventory/hosts`{{open}}

### Run our first ansible command

Check ansible controller_node facts

`ansible controller_node -i inventory -m setup`{{execute}}

```
$ ansible controller_node -i inventory -m setup
controller_node | success >> {
    "ansible_facts": {
        "ansible_all_ipv4_addresses": [
            "172.17.0.28"
        ], 
        "ansible_all_ipv6_addresses": [], 
        ...
```

Get inventory hosts list

`ansible all -i inventory --list-hosts`{{execute}}
