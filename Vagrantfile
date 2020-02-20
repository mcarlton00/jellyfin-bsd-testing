# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "jellyfin" do |jellyfin|
    jellyfin.vm.box = "bento/freebsd-12.1"

    jellyfin.vm.network "forwarded_port", guest: 8096, host: 8096

    jellyfin.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end
  end
end
