# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.forward_agent = true

  config.vm.define :webserver do |webserver|
    webserver.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--cpus", 1]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--name", "webserver"]
    end

    webserver.vm.box = "ubuntu/xenial64"
    webserver.vm.hostname = "webserver"

    webserver.vm.network :private_network, ip: "10.128.0.5"

    webserver.vm.provision "shell" do |shell|
      shell.inline = "apt-get install -y python"
    end

    webserver.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yaml"
    end
  end

end