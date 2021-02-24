Getting Started with Ansible

## The Inventory
To use the ansible command for host management, you need to provide an inventory file which defines a list of hosts to be managed from the control node. One way to do this is to specify the path to the inventory file with the `-i` option to the ansible command.


Create a directory for your Ansible inventory:

`mkdir  inventory`{{execute}}

Now create a simple inventory file as inventory/hosts with the following content:

```
cat << EOF > inventory/hosts
controller_node ansible_connection=local

EOF
```{{execute}}

Check the content of the inventory file `inventory/hosts`{{open}}

### Run our first ansible command

Check ansible facts
`ansible controller_node -i inventory -m setup`





`localhost`{{copy}}


host1.cloud.ws.afnog.org
host2.cloud.ws.afnog.org
To reference inventory hosts, you supply a host pattern to the ansible command. Ansible has a --list-hosts option which can be useful for clarifying which managed hosts are referenced by the host pattern in an ansible command.

The most basic host pattern is the name for a single managed host listed in the inventory file. This specifies that the host will be the only one in the inventory file that will be acted upon by the ansible command. Run:

[ansible@control ~]$ ansible "host1.cloud.ws.afnog.org" -i ~/ansible-files/inventory --list-hosts

  hosts (1):
    host1.cloud.ws.afnog.org
An inventory file can contain a lot more information, it can organize your hosts in groups or define variables. You will use grouping most of the times, change your inventory file to look like this:

[webserver]
host1.cloud.ws.afnog.org
