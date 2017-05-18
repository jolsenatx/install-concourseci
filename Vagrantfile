#Jumpbox with Cloud Foundry CLI installed
Vagrant.configure("2") do |config|
  config.vm.define "jumpbox" do |jumpbox|
    jumpbox.vm.box = "ubuntu/xenial64"
    jumpbox.vm.hostname = 'jumpbox'
    jumpbox.vm.box_url = "ubuntu/xenial64"
    jumpbox.vm.provision :shell, path: "bootstrap.sh"
    jumpbox.vm.provision :shell, path: "Do_install.sh"

    jumpbox.vm.network :private_network, ip: "192.168.99.100"

    jumpbox.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--name", "jumpbox"]
    end
  end

#Concourse CI VM
  config.vm.define "concourse" do |concourse|
    concourse.vm.box = "concourse/lite"
    concourse.vm.hostname = 'concourse'
    concourse.vm.box_url = "concourse/lite"

    concourse.vm.network :private_network, ip: "192.168.99.101"

    concourse.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 4096]
      v.customize ["modifyvm", :id, "--name", "concourse"]
    end
  end
end