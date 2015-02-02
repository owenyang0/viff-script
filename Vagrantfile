# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu1404"

  config.vm.define :viff do |master|
    master.vm.network "forwarded_port", guest: 80, host: 8088
    master.vm.network "forwarded_port", guest: 27017, host: 27017
    master.vm.network "forwarded_port", guest: 9999, host: 9999
    master.vm.network "forwarded_port", guest: 6379, host: 6379
    master.vm.network "forwarded_port", guest: 3000, host: 30000
    master.vm.network "forwarded_port", guest: 3001, host: 30001

    master.vm.hostname = "viff"
    master.vm.network "private_network", ip: "10.1.1.2"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./ansible-tasks/playbook.yml"
    ansible.verbose = "vvv"
  end
end
