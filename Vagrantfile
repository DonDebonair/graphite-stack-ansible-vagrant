# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "graphite" do |graphite|
    # graphite.vm.box = "centos-6-4"
    # graphite.vm.box_url = "https://dl.dropboxusercontent.com/s/z85s74gv74m6flo/centos-6-4.box"
    # graphite.vm.box = "wheezy64"
    # graphite.vm.box_url = "https://dl.dropboxusercontent.com/s/j887m9989t2g8zj/wheezy64.box"
    graphite.vm.box = "ubuntu/trusty64"
    graphite.vm.network :private_network, ip: "192.168.33.20"

    graphite.vm.provision "ansible" do |ansible| 
      ansible.playbook = "graphite.yml"
    end 
  end

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end

end
