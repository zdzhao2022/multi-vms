# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/centos7"

  config.vm.provision "file",
    source: "~/vagrant/files/git-config",
	destination: "~/.gitconfig"
	
  config.vm.provision "shell", 
    path: "https://raw.githubusercontent.com/zdzhao2022/vagrant/main/scripts/centos-common.sh"
     
  config.vm.define "web" do |web|
	web.vm.hostname = "web-server"
	web.vm.network "forwarded_port", guest: 80, host: 8080
	web.vm.network "private_network", ip: "192.168.10.2"
	web.vm.provision "shell", 
		path: "https://raw.githubusercontent.com/zdzhao2022/vagrant/main/scripts/centos-web.sh"
  
  end
  
  config.vm.define "db" do |db|
	db.vm.hostname = "database-server"
	db.vm.network "private_network", ip: "192.168.10.3"
	db.vm.provision "shell", 
		path: "https://raw.githubusercontent.com/zdzhao2022/vagrant/main/scripts/centos-database.sh"
  
  end
  
end
