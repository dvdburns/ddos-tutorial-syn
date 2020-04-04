# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "attacker" do |vm1|
    vm1.vm.hostname = "attacker"
    vm1.vm.box = "ubuntu/xenial64"
    vm1.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-1",
      auto_config: false

    vm1.vm.provider "virtualbox" do |vb|
      vb.name = "attacker"
      vb.gui = false
      vb.memory = "512"
    end

    vm1.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Attacker is online!"
    SHELL
  end

  config.vm.define "defender" do |vm2|
    vm2.vm.hostname = "defender"
    vm2.vm.box = "ubuntu/xenial64"
    vm2.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-2",
      auto_config: false

    vm2.vm.provider "virtualbox" do |vb|
      vb.name = "defender"
      vb.gui = false
      vb.memory = "512"
    end

    vm2.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Defender is online!"
    SHELL
  end

   config.vm.define "attacker-router" do |router1|
    router1.vm.hostname = "attacker-router"
    router1.vm.box = "ubuntu/xenial64"
    router1.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-1",
      auto_config: false
    router1.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-100",
      auto_config: false

    router1.vm.provider "virtualbox" do |vb|
      vb.name = "attacker-router"
      vb.gui = false
      vb.memory = "1024"
    end

    router1.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Attacker Router online!"
    SHELL
  end

  config.vm.define "defender-router" do |router2|
    router2.vm.hostname = "defender-router"
    router2.vm.box = "ubuntu/xenial64"
    router2.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-2",
      auto_config: false
    router2.vm.network "private_network", type:"dhcp", virtualbox__intnet: "intnet-100",
      auto_config: false

    router2.vm.provider "virtualbox" do |vb|
      vb.name = "defender-router"
      vb.gui = false
      vb.memory = "1024"
    end

    router2.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Defender Router online!"
    SHELL
  end

end
