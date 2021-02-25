## Running Playbooks

Playbooks are executed using the `ansible-playbook` command on the control node. Before you run a new Playbook it’s a good idea to check for syntax errors:

`ansible-playbook --syntax-check apache.yml`{{execute T2}}

Now you should be ready to run your Playbook, but first let's check that the Package isn’t yet installed:

`dpkg-query -W -f='${Status} ${Version}\n' apache2`{{execute T2}}

Or even better use an Ansible ad hoc command!

`ansible runner -m shell -a "dpkg-query -W -f='${Status} ${Version}\n' apache2"`{{execute T2}}

Now it is time to run our playbook:

`ansible-playbook apache.yml`{{execute T2}}

Let's check if package Apache is now install as expected:

`ansible runner -m shell -a "dpkg-query -W -f='${Status} ${Version}\n' apache2"`{{execute T2}}
