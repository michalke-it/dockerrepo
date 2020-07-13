# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "dockerrepo"
  config.disksize.size = '15GB'
  config.vm.network "public_network", bridge: "enp5s0f0"
  config.vm.provider "virtualbox" do |v|
    v.name = "dockerrepo"
    v.memory = 1024
    v.cpus = 1
    v.gui = false
  end
  config.vm.provision :shell, inline: "sudo wget -qO- https://get.docker.com/ | sh"
  config.vm.provision :shell, inline: 'sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
  config.vm.provision :shell, inline: "sudo chmod +x /usr/local/bin/docker-compose"
  config.vm.provision :shell, inline: "docker-compose -f /vagrant/repo.yml up -d"
end
