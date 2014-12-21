# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Uncomment one of the boxes below depending on the box you currently have.
  # If you don't have either box, uncomment the first one.
  # To find which boxes are on your system: $ vagrant box list
  #config.vm.box = "drifty/ionic-android"
  #config.vm.box = "drifty_ionic"

  # Forward the ports used by Ionic for testing and development
  # These ports are obtained when running the Ionic project: $ ionic serve
  config.vm.network "forwarded_port", guest: 8100, host: 8100
  config.vm.network "forwarded_port", guest: 35729, host: 35729

  # Specifies the mapped folder in the Vagrant VM.
  # The following expects that that "ionic_wya" project is cloned into a
  #  sibling directory to the current directory for this Vagrantfile.
  config.vm.synced_folder "../ionic_wya", "/project"

  # Updates Ionic to the most current version on provisioning of the VM
  config.vm.provision "shell",
    inline: "sudo npm update -g ionic"
end
