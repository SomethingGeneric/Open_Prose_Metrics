# -*- mode: ruby -*-
# vi: set ft=ruby :
$ram = 8096
$cpus = 4
$http_port = 9090
$ft_port = 5002

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.network "forwarded_port", guest: 80, host: $http_port
  config.vm.network "forwarded_port", guest: 5000, host: $ft_port
  config.vm.provision "shell", path: "deploy.sh"
  config.vm.provision "shell", path: "wsgi-install.sh"
  config.vm.provider :virtualbox do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:

    vb.customize ["modifyvm", :id, "--memory", $ram, "--cpus", $cpus]
  end
end
