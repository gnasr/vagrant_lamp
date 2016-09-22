# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "lamp"
  config.vm.network "private_network", ip: "192.168.150.10"
<<<<<<< HEAD
  config.vm.synced_folder "webapp/", "/var/www/webapp", create: true
=======
  config.vm.synced_folder "webapp/", "/var/www/", create: true
>>>>>>> 3ed3d4b5acf1bcfcd79c3762fc170d1694733f3a
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/ansible_hosts"
<<<<<<< HEAD
=======
    ansible.sudo = "true"
>>>>>>> 3ed3d4b5acf1bcfcd79c3762fc170d1694733f3a
    ansible.limit = "all"
  end

end
