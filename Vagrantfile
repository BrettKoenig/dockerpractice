# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
    install_docker = %Q{
      if [ ! $(which docker) ]; then
        sudo apt update
        sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
        sudo apt update
        sudo apt install -y docker-ce
      else
        echo "docker already installed."
      fi
    }
  
  
    config.vm.define "host1" do |node|
      node.vm.box = "silverhighway/zesty64"
      node.vm.hostname = "host1"
      node.vm.network "private_network", ip: "192.168.50.2"
      node.vm.provider :virtualbox do |vb|
        vb.customize ['modifyvm', :id, '--memory', '1024']
      end

      node.vm.provision "shell", inline: install_docker
    end
  end
  