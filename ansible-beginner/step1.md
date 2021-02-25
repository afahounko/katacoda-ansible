Check the prerequisites and create our working directory to organise our ansible roles and playbooks.

## Prerequisites

Upgrade python `pip`

`pip3 install --upgrade pip`{{execute}}

Install `ansible` package

`pip3 install ansible`{{execute}}

Check the version of `ansible`  with the following command:

`ansible --version`{{execute}}

You will see the version of Ansible
```
$ ansible --version
ansible 2.10.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.8/dist-packages/ansible
  executable location = /usr/local/bin/ansible
  python version = 3.8.6 (default, Oct  6 2020, 03:22:36) [GCC 7.5.0]
```

### Working directory

Let's organise our work by creating our working directory

`mkdir  learn-ansible`{{execute T2}}

`cd  learn-ansible`{{execute T2}}

Now we are ready to start our workshop.