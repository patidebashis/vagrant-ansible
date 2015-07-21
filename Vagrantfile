# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network :public_network

  config.vm.define "master" do |master|
      master.vm.box = "precise32"
      master.vm.box_url = "http://files.vagrantup.com/precise32.box"
      master.vm.hostname = "master"
      master.vm.network :forwarded_port, guest: 8080, host: 1234
      master.vm.network "private_network", ip: "192.168.50.1"
      master.vm.provision "ansible" do |ansible|
          ansible.playbook = "master.yml"
      end
  end

end
