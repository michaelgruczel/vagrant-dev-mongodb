# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  config.vm.box = "ubuntu12041-shop-middleware"
  config.vm.box_url = "http://dl.dropbox.com/u/4031118/Vagrant/ubuntu-12.04.1-server-i686-virtual.box"  
  config.vm.network :forwarded_port, guest: 27017, host: 27018

  #config.vm.synced_folder "./vagrantdata", "/vagrantdata"
  config.vm.provider :virtualbox do |vb|
    vb.gui = false
  end
  
  config.vm.provision :shell, :inline => "apt-get update"
  # Otherwise java install will fail with missing dependencies  
  config.vm.provision :shell, :inline => "sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10"
  config.vm.provision :shell, :inline => "echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list"
  config.vm.provision :shell, :inline => "sudo apt-get update"
  config.vm.provision :shell, :inline => "sudo apt-get install -y mongodb-10gen"
  config.vm.provision :shell, :inline => "sudo service mongodb start"

end
