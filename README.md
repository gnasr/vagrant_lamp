# vagrant_lamp
This Vagrantfile will deploy a virtual machine with apache, php and mysql.
A shared folder called 'webapp' is setup so you can easily deploy your webapp into '/var/www'

In order to use this Vagrantfile, first you need to:

1. Install Virtualbox
2. Install Vagrant
3. Install Ansible

##The Ansible playbook requires:
* geerlingguy.apache
* geerlingguy.mysql
* geerlingguy.php

To install this roles, you must enter in ansible folder and run the following command:
`ansible-galaxy install -r roles/roles_requirements.yml`.

##Defaults:
* apache_listen_port: 80
* mysq_enabled_on_startup: yes
