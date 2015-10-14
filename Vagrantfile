# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
  end

  config.vm.provision "shell", inline: <<-SHELL
    set -ex
    sudo apt-get update
    sudo apt-get install -y iperf
  SHELL

  config.vm.define :server do |server|
    server.vm.hostname = "iperf-server"
    server.vm.network "private_network", ip: "192.168.33.10"
  end

  config.vm.define :client do |client|
    client.vm.hostname = "iperf-client"
    client.vm.network "private_network", ip: "192.168.33.11"
  end
end
