# vagrant_lamp
This Vagrantfile will deploy a virtual machine with the ip 192.168.150.10, then will configure it as a lamp server.
A shared folder called 'webapp' is setup so you can easily deploy your webapp into '/var/www'

##Instructions
In order to use this Vagrantfile, first you need to:

1. [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. [Install Virtualbox](https://www.virtualbox.org/wiki/Downloads)
3. [Install Vagrant](https://www.vagrantup.com/docs/installation/)
4. [Install Ansible](https://docs.ansible.com/ansible/intro_installation.html)

Then, run the following commands in a terminal
```
git clone https://github.com/gnasr/vagrant_lamp.git
cd vagrant_lamp
```
To install php, apache and mysql this Vagrantfile uses Ansible as provisioner, so you must install the ansible playbook requirements

##The Ansible playbook requires:
* geerlingguy.apache
* geerlingguy.mysql
* geerlingguy.php

You can install this roles using `ansible-galaxy`:
```
cd ansible
ansible-galaxy install -r roles/roles_requirements.yml
```

Now you are ready to start the virtual machine:
```
vagrant up
```

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
|```mysql_root_password```|123456|
