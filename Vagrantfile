# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "fgrehm/trusty64-lxc"
  config.vm.box_check_update = false

  config.vm.provision "shell", inline: <<-SHELL
    set -ex
    sudo apt-get update
    sudo apt-get install -y iperf
  SHELL

  config.vm.define :server do |server|
    server.vm.hostname = "iperf-server"
    server.vm.network "private_network", ip: "192.168.33.10", lxc__bridge_name: 'lxcbr1'
  end

  config.vm.define :client do |client|
    client.vm.hostname = "iperf-client"
    server.vm.network "private_network", ip: "192.168.33.11", lxc__bridge_name: 'lxcbr1'
  end
end
