## Extend the playbook: Add index.html template

Create the file index.tpl:

```
cat << EOF > index.tpl
<body>
	<h1>Apache is running fine thanks to Ansible!</h1>
  <h2>Web server on {{ inventory_hostname }} </h2>
</body>
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/index.tpl`{{open}}

Update the file `apache.yml` to replace the third task using the module copy with template.

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
  - name: copy index.tpl
    template:
      src: ${PWD}/index.tpl 
      dest: /var/www/html/index.html
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/apache.yml`{{open}}

Now it is time to run our extended playbook:

`ansible-playbook apache.yml`{{execute T2}}

## Check the default web page

`curl localhost`{{execute}}

Or

Click on the `New Tab` button on the Terminal and open `view HTTP port 80 on Host 1` 

