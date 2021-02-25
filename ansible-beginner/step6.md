## Extend the playbook: Enable service

Update the file `apache.yml` to add a second task using the service module.
a second task is defined
a module is specified (service)

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
  - name: Apache enabled and running
    service:
      name: apache2
      enabled: true
      state: started
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/apache.yml`{{open}}

Now it is time to run our extended playbook:

`ansible-playbook apache.yml`{{execute T2}}

## Check the default web page

`curl localhost`{{execute}}

Or

Click on the `New Tab` button on the Terminal and open `view HTTP port 80 on Host 1` 