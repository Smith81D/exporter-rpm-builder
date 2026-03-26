# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  #config.vm.box = "cloud-image/fedora-43"
  config.vm.box = "cloud-image/rocky-8"

  # Helper to set RAM & CPUs
  def configure_resources(vm_config)
#    vm_config.vm.provider "virtualbox" do |vb|
    vm_config.vm.provider "libvirt" do |vb|
      vb.memory = 16384   # 16 GB
      vb.cpus = 4         # 4 cores
    end
  end

  config.vm.define "RpmBox" do |vm|
    vm.vm.hostname = "RpmBox"
  
    # Main IP for Ansible/SSH
    vm.vm.network "private_network", ip: "192.168.56.3"
  
    configure_resources(vm)
  
    # Forward custom port (optional)
    # vm.vm.network "forwarded_port", guest: 19391, host: 19391, auto_correct: true, host_ip: "127.0.0.1"
  
    # Provision with Ansible
    vm.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.limit = "all"
      ansible.inventory_path = "inventory/vagrant.ini"
      ansible.verbose = "v"
    end
  end
end

