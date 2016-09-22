# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "lamp"
  config.vm.network "private_network", ip: "192.168.150.10"
  config.vm.synced_folder "webapp/", "/var/www/webapp", create: true
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/ansible_hosts"
    ansible.limit = "all"
  end

end
