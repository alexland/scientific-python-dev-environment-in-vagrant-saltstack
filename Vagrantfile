# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box = "precise64"
	config.vm.box_url = "http://files.vagrantup.com/precise64.box"

	# salt provisioner
	config.vm.provision :salt do |salt|
		
		# relative location of configuration file to use for minion
		# since we need to tell our minion to run in masterless mode
		# ie, tell the minions *not* to look for a master 
		salt.minion_config = "saltstack/etc/minion"

		# to install packages, services, etc, on provision, run state.highstate 
		# 'highstate': diff VMs current machine state 
		# against what it should be & make any require changes
		salt.run_highstate = true

		# install salt, specify install source & version
		salt.install_type = "git"
		salt.install_args = "v2014.1.0"

		salt.verbose = true
	end
end