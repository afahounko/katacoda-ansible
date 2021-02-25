## Your first Playbook

Enough theory, it’s time to create your first Playbook. In this lab you create a Playbook to set up an Apache webserver in three steps:

First step: Install apache2 package
Second step: Enable/start httpd service
Third step: Create an index.html file

### Playbook: Install Apache

This Playbook makes sure the package containing the Apache webserver is installed on `localhost`.

TIP: You obviously need to use privilege escalation to install a package or run any other task that requires root permissions. This is done in the Playbook by `become: yes`.

Create the file `apache.yml` with the following content

```
cat << EOF > apache.yml
---
- name: Apache server installed
  hosts: runner
  become: yes
  tasks:
  - name: latest Apache version installed
    package:
      name: apache2
      state: latest
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/apache.yml`{{open}}

