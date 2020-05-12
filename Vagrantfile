# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/alpine310"# "alpine/alpine64"

  config.vm.box_check_update = true

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  config.vm.network "private_network", ip: "192.168.33.10"
  #config.vm.network "private_network", type: "dhcp"
  # config.vm.network "public_network"
  config.vbguest.auto_update = false
  config.vbguest.no_remote = true
  config.vm.synced_folder "../.", "/vagrant_data", type: "nfs"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
  end

  config.vm.provision "shell", inline: <<-SHELL
    apk update
    apk upgrade
    apk add vim htop docker docker-compose git make
    rc-update add docker boot
    service docker start
    groupadd docker
    gpasswd -a vagrant docker
  SHELL
end
