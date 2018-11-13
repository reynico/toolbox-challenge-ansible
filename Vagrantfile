# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 80, host: 8000
  config.vm.provision "file", source: "ansible", destination: "/home/vagrant/ansible"

  config.vm.provision "shell", inline: <<-SHELL
	echo "Installing required packages"
    sudo yum update -y
	sudo yum install -y epel-release ansible
	easy_install pip
	ansible-playbook -l localhost ansible/playbook.yml
	echo "Environment provisioning complete. Web server available at http://localhost:8000"
  SHELL
end
