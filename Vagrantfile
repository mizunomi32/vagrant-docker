# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/alpine310"# "alpine/alpine64"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.hostsupdater.aliases = ["apollon.world.localhost"]
  config.vm.box_check_update = true
  config.vbguest.auto_update = false
  config.vbguest.no_remote = true
  config.vm.synced_folder "../.", "/home/vagrant/src", type: "nfs"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
    vb.cpus = 4
    vb.customize [
      "modifyvm", :id,
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--ioapic", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]
  end

  config.vm.provision "shell", inline: <<-SHELL
    apk update
    apk upgrade
    apk add vim htop docker docker-compose git make shadow
    rc-update add docker boot
    service docker start
    usermod -aG docker vagrant
  SHELL
end
