# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "fbertola/elementaryos-0.4-amd64"
  config.vm.guest = :ubuntu
  config.ssh.username = "vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "deviant"

    # Display the VirtualBox GUI when booting the machine
    vb.gui = true

    # Customize the amount of memory on the VM:
    vb.memory = 2048

    # Customize the amount of cores allocated
    vb.cpus = 2
  end

  config.vm.hostname = "deviant"

  # Set the name of the virtual machine
  config.vm.define :deviant do |deviant|
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
  end

end
