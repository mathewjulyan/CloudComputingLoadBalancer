# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 256]
  end

  config.vm.define :haproxy, primary: true do |haproxy_config|

    haproxy_config.vm.hostname = 'haproxy'
    haproxy_config.vm.network :forwarded_port, guest: 8080, host: 8080
    haproxy_config.vm.network :forwarded_port, guest: 80, host: 8081

    haproxy_config.vm.network :private_network, ip: "172.28.33.10"
    haproxy_config.vm.provision :shell, :path => "haproxy-setup.sh"

  end
end
