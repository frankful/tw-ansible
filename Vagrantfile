# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--name", "xxl-job", "--memory", "512"]
  end
  config.vm.box = "ubuntu14"
  config.vm.hostname = "xxl-job"
  config.ssh.username = "deploy"
  config.ssh.password = "deploy"
  config.ssh.insert_key = false
#  config.ssh.private_key_path = "/data/tw-pro/templates/rsakey/git.deploy.id_rsa"
  # config.vm.synced_folder "../data", "/vagrant_data"
#  config.vm.network "public_network", ip: "10.0.2.10"
  config.vm.network "private_network", ip: "10.0.0.10"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provision :ansible do |ansible|
      ansible.playbook = "deploy-tw-java.yml"
    end
end
