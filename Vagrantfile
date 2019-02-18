# -*- mode: ruby -*-
# vi: set ft=ruby :

# require 'json'

Vagrant.configure(2) do |config|


  config.vm.provider "virtualbox" do |vb|
    vb.name = "4545-tools"

    config.vm.box = "ubuntu/bionic64"
    config.vm.network "forwarded_port", guest: 8000, host: 8000
    config.vm.hostname = "vagrant4545"
    config.ssh.forward_agent = true

    config.vm.provision :shell, :path => "./initial-setup.sh", run: "once", privileged: false
    config.vm.provision :shell, :path => "./startup.sh", run: "always", privileged: false
  end


  config.vm.provider :google do |google, override|
    config.vm.box = "google/gce"
    google.machine_type = "f1-micro"
    google.zone = "us-east1"
    google.google_project_id = "crazyhouse4545"
    google.google_client_email = "vagrant@crazyhouse4545.iam.gserviceaccount.com"
    google.google_json_key_location = "/Users/colwem/workshop/4545vagrant/CrazyHouse4545-d17a247f6a9a.json"

    google.image_family = 'ubuntu-1804-lts'
    
    override.ssh.username = "colwem"
    override.ssh.private_key_path = "~/.ssh/google_compute_engine"
  end

end
