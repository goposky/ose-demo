# -*- mode: ruby -*-
# vi: set ft=ruby :

# The private network IP of the VM. You will use this IP to connect to OpenShift.
# This variable is ignored for Hyper-V provider.

# Number of virtualized CPUs
#VM_CPU = ENV['VM_CPU'] || 2

# Validate required plugins
REQUIRED_PLUGINS = %w(vagrant-service-manager vagrant-registration vagrant-sshfs)
errors = []

def message(name)
  "#{name} plugin is not installed, run `vagrant plugin install #{name}` to install it."
end
# Validate and collect error message if plugin is not installed
REQUIRED_PLUGINS.each { |plugin| errors << message(plugin) unless Vagrant.has_plugin?(plugin) }
unless errors.empty?
  msg = errors.size > 1 ? "Errors: \n* #{errors.join("\n* ")}" : "Error: #{errors.first}"
  fail Vagrant::Errors::VagrantError.new, msg
end


Vagrant.configure(2) do |config|


  config.vm.box = 'rhel7-vagrant'
  config.ssh.forward_agent = true
  config.ssh.insert_key = false
  config.registration.username = ENV['SUB_USERNAME']
  config.registration.password = ENV['SUB_PASSWORD']


  config.vm.define "storage" do |storage|
    storage.vm.hostname = "storage"
    storage.vm.network "private_network", ip: "10.1.2.17", auto_config: false
    #storage.vm.network "forwarded_port", id: 'ssh', guest: 22, host: 2020, auto_correct: true
    storage.vm.provider "virtualbox" do |v, override|
      #v.cpus   = VM_CPU
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end
  end

  config.vm.define "node1" do |node1|
    node1.vm.hostname = "node1"
    node1.vm.network "private_network", ip: "10.1.2.16", auto_config: false
    #node1.vm.network "forwarded_port", id: 'ssh', guest: 22, host: 2020, auto_correct: true
    node1.vm.provider "virtualbox" do |v, override|
      #v.cpus   = VM_CPU
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end
  end

  config.vm.define "master", primary: true do |master|
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "10.1.2.15", auto_config: false
    master.vm.provider "virtualbox" do |v, override|
      #v.cpus   = VM_CPU
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end
  end

  #config.vm.provision "shell", run: "always", inline: <<-SHELL
    # Do something
  #SHELL
end
