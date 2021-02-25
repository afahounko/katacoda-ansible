## Extend the playbook: Add index.html page

Create the file index.html:

```
cat << EOF > index.html
<body>
	<h1>Apache is running fine thanks to Ansible!</h1>
</body>
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/index.html`{{open}}

Update the file `apache.yml` to add a third task using the module copy.

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
  - name: copy index.html
    copy:
      src: ${PWD}/index.html 
      dest: /var/www/html/
EOF
```{{execute T2}}

Check the content of the config file `learn-ansible/apache.yml`{{open}}

Now it is time to run our extended playbook:

`ansible-playbook apache.yml`{{execute T2}}

## Check the default web page

`curl localhost`{{execute}}

Or

Click on the `New Tab` button on the Terminal and open `view HTTP port 80 on Host 1` 

