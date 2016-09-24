# vagrant_lamp
This Vagrantfile will deploy a virtual machine with apache, php and mysql.
A shared folder called 'webapp' is setup so you can easily deploy your webapp into '/var/www'

##Instructions
In order to use this Vagrantfile, first you need to:

1. Install Git
2. Install Virtualbox
3. Install Vagrant
4. Install Ansible

Run the following commands in a terminal
```
git clone https://github.com/gnasr/vagrant_lamp.git
cd vagrant_lamp
cd ansible
```
To install php, apache and mysql this Vagrantfile uses Ansible as provisioner, so you must install the ansible playbook requirements

##The Ansible playbook requires:
* geerlingguy.apache
* geerlingguy.mysql
* geerlingguy.php

To install this roles, you must run the following commands:
```
cd ansible
ansible-galaxy install -r roles/roles_requirements.yml
```

Now you are ready to run the virtual machine just one more command:
`vagrant up`

Vagrant will download an Ubuntu 14.04 image and create the virtual machine, then ansible will configure the services.
* To test if apache and php were installed successfully you need to enter this url in your web browser
`http://192.168.150.10/`
You must see a web page showing the info of the php version installed.
* To test mysql enter in your terminal, (use the default password):
```
vagrant ssh
mysql -u root -p -e "SELECT @@version;"
```
You should see something like:
```
+-------------------------+
| @@version               |
+-------------------------+
| 5.5.52-0ubuntu0.14.04.1 |
+-------------------------+
```
##Roles variables:

|Variable|Default|
|---|:--|
|```apache_listen_port```|80|
|```mysql_enabled_on_startup```|yes|
|```mysql_root_password```|root|
