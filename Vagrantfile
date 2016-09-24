# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "lamp"
  config.vm.network "private_network", ip: "192.168.150.10"
  config.vm.synced_folder "webapp/", "/var/www/webapp", create: true
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/lamp.yml"
    ansible.inventory_path = "ansible/vagrant_hosts.ini"
    ansible.limit = "all"
  end

end
