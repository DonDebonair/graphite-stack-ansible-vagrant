VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "monitoring" do |monitoring|
    # graphite.vm.box = "centos/7"
    # graphite.vm.box = "debian/jessie64"
    monitoring.vm.box = "ubuntu/xenial64"
    monitoring.vm.network :private_network, ip: "172.0.0.10"

    monitoring.vm.provision "ansible_local" do |ansible| 
      ansible.playbook = "monitoring.yml"
      # ansible.raw_arguments = ["-vvv"]
    end 
  end

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end

end
