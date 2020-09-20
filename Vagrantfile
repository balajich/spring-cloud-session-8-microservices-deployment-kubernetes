# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

  config.vm.define "kubernetes" do |kubernetes|
    kubernetes.vm.box = "centos/7"
    kubernetes.vm.hostname = "kubernetes.eduami.org"
    kubernetes.vm.network "private_network", ip: "192.168.50.26"
    #kubernetes.vm.network "forwarded_port", guest: 8080, host: 8080
    #kubernetes.vm.network "forwarded_port", guest: 8761, host: 8761
    kubernetes.vm.network "forwarded_port", guest: 5672, host: 5672
    kubernetes.vm.network "forwarded_port", guest: 15672, host: 15672
    kubernetes.vm.network "forwarded_port", guest: 9411, host: 9411
    kubernetes.vm.provision "shell", path: "startup-kubernetes.sh"
    kubernetes.vm.provider "virtualbox" do |vb|
      vb.name = "kubernetes"
      vb.memory = 4024
      vb.cpus = 4
    end
  end
end
