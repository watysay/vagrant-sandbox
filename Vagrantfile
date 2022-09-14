# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vbguest.auto_update = false
  config.vbguest.no_install = true
  
  #config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.synced_folder ".", "/vagrant"

  config.vm.define "rocky8" do |sb|
    sb.vm.box = "generic/rocky8"
    #sb.vm.box_version = "4.1.12"
    
    sb.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 512
    end

    sb.vm.provision "shell" do |s|
      s.inline = "dnf install -y wget"
    end
  end

  config.vm.define "ubuntu" do |sb|
    sb.vm.box = "ubuntu/jammy64"
    
    sb.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 512
    end
    
    #sb.vm.provision "shell", path: "install_molecule.sh", privileged: false
  end

  config.vm.define "molecule" do |sb|
    sb.vm.box = "ubuntu/22.04-molecule4.0.1"
    sb.vm.network "forwarded_port", guest: 80, host: 8888

    sb.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 512
    end

  end

  config.vm.define "centos7" do |sb|
    sb.vm.box = "generic/centos7"
    #sb.vm.box_version = "4.1.12"
    
    sb.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 512
    end
  end

end

