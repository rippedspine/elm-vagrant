# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  hostname = "elm.box"

  # Box
  config.vm.box = "ubuntu/vivid64"

  config.vm.network :forwarded_port, host: 5000, guest: 8000
  config.vm.synced_folder ".", "/vagrant"

  # Lang
  config.vm.provision :shell, :inline => "apt-get install -q -y nodejs-legacy"
  config.vm.provision :shell, :inline => "apt-get install -q -y npm"
  config.vm.provision :shell, :inline => "npm install --global elm"

  # Hack to fix elm-package installs in Vagrant box, see https://github.com/elm-lang/elm-package/issues/115
  # We need to install each dependency manually $ elm-install elm-lang/core 2.0.0
  config.vm.provision :shell, :inline => "chmod +x /vagrant/elm-install.py; alias elm-install='/vagrant/elm-install.py'"

  # VirtualBox
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end
end
