# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/12"

    config.vm.provider "virtualbox" do |vb|
      # Customize the amount of memory on the VM:
      vb.memory = "1024"
      vb.customize ['modifyvm', :id, '--nested-hw-virt', 'on']
    end

    config.vm.provision "shell", 
      inline: "sudo apt update; apt -y install avahi-daemon avahi-utils libnss-mdns"

    config.vm.define "srv" do |server|
      server.vm.hostname = "srv"
      server.vm.network(:private_network, ip: "192.168.50.11")
    end 

    config.vm.define "cli" do |client|
      client.vm.hostname = "cli"
      client.vm.network(:private_network, ip: "192.168.50.12")
    end

end
