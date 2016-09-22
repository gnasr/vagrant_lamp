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

You can install this roles inside this folder or in ansible's default roles path, with the following command:
`ansible-galaxy install -r requirements.yml`.

For example, to install the roles in this folder:
``` 
mkdir -p roles
ansible-galaxy install -r requirements.yml --roles-path=./roles
```

##Defaults:
* apache_listen_port: 80
* mysql_root_password: 123456
* mysq_enabled_on_startup: yes
