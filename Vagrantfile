# * mode: ruby *
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "ciserver" do |ciserver|
    ciserver.vm.box = "geerlingguy/centos7"
    ciserver.vm.host_name = 'jenkins'
    ciserver.vm.network :forwarded_port, guest: 8080, host: 8080
    ciserver.vm.network "private_network", ip: "192.168.50.104"
    ciserver.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/hosts"
      ansible.verbose = "vvv"
    end
  end
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
end
