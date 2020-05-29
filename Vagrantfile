# -*- mode: ruby -*-
# vi: set ft=ruby :


$script_centos = <<-SCRIPT
sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
systemctl restart sshd
echo "root:password" | sudo chpasswd
SCRIPT


Vagrant.configure("2") do |config|
  config.vbguest.auto_update = false

  config.vm.define "centos1" do |centos1|
    centos1.vm.box = "centos/7"
    centos1.vm.provider "virtualbox" do |vb|
      vb.cpus = "1"
      vb.memory = "2048"
      vb.gui = false
    end
    centos1.vm.hostname = "projectl"
    centos1.vm.network "private_network", ip: "192.168.56.10"
	centos1.vm.provision "shell", "inline": $script_centos
  end
end
