# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
NETWORK_FILE_SYSTEM = false

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.ssh.forward_agent = true
  config.vm.synced_folder "./src", "/srv/", :nfs => NETWORK_FILE_SYSTEM

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  config.vm.define "wordpress-app" do |node|
    node.vm.hostname = "wordpress.dev"
    node.vm.network :private_network, ip: "192.168.42.100"
    node.hostmanager.aliases = %w(wordpress.dev)
  end

   config.vm.provider "virtualbox" do |vb|
     vb.customize ["modifyvm", :id, "--memory", "2048"]
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
   end

   config.vm.provision "ansible" do |ansible|
     ansible.limit = "local"
     ansible.inventory_path = "hosts.local"
     ansible.playbook = "site.yml"
   end

end