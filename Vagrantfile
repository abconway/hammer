# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.forward_agent = true

  config.vm.define :node do |node|
    node.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--cpus", 1]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--name", "node"]
    end

    node.vm.box = "ubuntu/xenial64"
    node.vm.hostname = "node"

    node.vm.network :private_network, ip: "10.128.0.5"

    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yaml"
    end
  end

end