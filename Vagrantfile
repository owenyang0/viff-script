# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu1404"

  config.vm.define :viff do |master|
    master.vm.network "forwarded_port", guest: 80, host: 8088
    master.vm.network "forwarded_port", guest: 27017, host: 27017

    master.vm.hostname = "viff"
    master.vm.network "public_network", ip: "10.17.2.22"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./ansible-tasks/playbook.yml"
  end
end
