# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "Windows" do |windows|
    windows.vm.box = "gusztavvargadr/windows-server"
    windows.vm.network "private_network", type: "static", ip: "192.168.1.5"
    windows.vm.hostname = "WinServ"
    windows.vm.provider "virtualbox" do |v|
      v.name = "dc03"
      v.memory = 4096
      v.cpus = 2
    end
    
    windows.vm.provision "shell", path: "winrm.ps1"

    windows.vm.provision "shell",
      inline: "Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False"

    windows.vm.provision "shell",
      inline: "ansible-playbook -i host.ini create_dc0.yml"

    end
  end
end
