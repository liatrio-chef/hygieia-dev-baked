# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  #
  # hygieia-dev
  #
  config.vm.define "hygieia", :primary => true do |hygieia|
    hygieia.vm.box = "liatrio/hygieia-dev"

    hygieia.vm.hostname = 'hygieia-dev'
    hygieia.vm.network :private_network, ip: "192.168.100.10"
    hygieia.vm.network :forwarded_port, guest: 22, host: 2210, id: "ssh"
    hygieia.vm.network :forwarded_port, guest: 8081, host: 18081 # archiva
    hygieia.vm.network :forwarded_port, guest: 9000, host: 19000 # sonarqube
    hygieia.vm.network :forwarded_port, guest: 8082, host: 18082 # tomcat
    hygieia.vm.network :forwarded_port, guest: 8083, host: 18083 # jenkins
    hygieia.vm.network :forwarded_port, guest: 3000, host: 13000 # hygieia
    hygieia.vm.network :forwarded_port, guest: 8080, host: 18080 # hygieia-api
    hygieia.vm.network :forwarded_port, guest: 27017, host: 37017 # mongodb

    hygieia.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--cpus", 2]
      v.customize ["modifyvm", :id, "--memory", 1536]
      #v.customize ["modifyvm", :id, "--name", "hygieia-liatrio"]
    end

    #hygieia.vm.provision "shell", inline: "touch /root/test"

  end

end
