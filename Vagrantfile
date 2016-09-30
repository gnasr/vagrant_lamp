# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "metrics" do |metrics|
    metrics.vm.box = "ubuntu/trusty64"
    metrics.vm.hostname = "metrics"
    metrics.vm.network "private_network", ip: "192.168.150.10"

    metrics.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/plays/metrics.yml"
      ansible.inventory_path = "ansible/vagrant_hosts.ini"
      ansible.limit = "all"
    end
  end

  config.vm.define "database" do |database|
    database.vm.box = "ubuntu/trusty64"
    database.vm.hostname = "database"
    database.vm.network "private_network", ip: "192.168.150.11"

    database.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/plays/database.yml"
      ansible.inventory_path = "ansible/vagrant_hosts.ini"
      ansible.limit = "all"
    end
  end

  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/trusty64"
    webserver.vm.hostname = "webserver"
    webserver.vm.network "private_network", ip: "192.168.150.12"
    webserver.vm.synced_folder "webapp/", "/var/www/webapp", create: true

    webserver.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/plays/webserver.yml"
      ansible.inventory_path = "ansible/vagrant_hosts.ini"
      ansible.limit = "all"
    end
  end

end
