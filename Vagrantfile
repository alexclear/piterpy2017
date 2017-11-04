# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "python-perf" do |server|
    server.vm.box = "bento/ubuntu-16.04"
    server.vm.hostname = "python-perf"
    #server.vm.network "private_network", type: "dhcp"

    server.vm.provider :virtualbox do |v, override|
      v.gui = false
      v.customize ["modifyvm", :id, "--cpus", 2]
      v.customize ["modifyvm", :id, "--memory", 1024]
      #v.customize ["modifyvm", :id, "--cableconnected1", "on"]
      #v.customize ["modifyvm", :id, "--cableconnected2", "on"]
    end

    server.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/perf.yml"
      ansible.become = true
    end
  end
end
