# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.

  config.vm.define :server do |server|
        server.vm.host_name = "bacula-server"
        server.vm.box = "bacula-client"
        config.vm.network :private_network, ip: "192.168.33.11"
        config.vm.provision :ansible do |ansible_server|
              ansible_server.playbook = "provisioning/bacula-server_playbook.yml"
              ansible_server.inventory_path = "provisioning/hosts-vagrant"
              ansible_server.verbose = false
            end
      end

  config.vm.define :client do |client|
        client.vm.host_name = "bacula-client"
        client.vm.box = "bacula-client"
        config.vm.network :private_network, ip: "192.168.33.10"
        config.vm.provision :ansible do |ansible_client|
              ansible_client.playbook = "provisioning/bacula-client_playbook.yml"
              ansible_client.inventory_path = "provisioning/hosts-vagrant"
              ansible_client.verbose = false
            end
      end

  end

