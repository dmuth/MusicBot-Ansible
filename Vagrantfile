# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|


	config.vm.define "ubuntu14.04" do |host|

		host.vm.box = "ubuntu/trusty64"

		#
		# Stick with the default insecure key so that we can Ansible to 
		# configure this instance.
		#
		host.ssh.insert_key = false

		#
		# Cache packages we download on the host machine
		#
		if Vagrant.has_plugin?("vagrant-cachier")
			host.cache.scope = :box
		end

		#
		# Disable updating the guest extensions because this is usually 
		# more trouble than it's worth.
		#
		if Vagrant.has_plugin?("vagrant-vbguest")
			host.vbguest.auto_update = false
		end

		host.vm.network "forwarded_port", guest: 80, host: 8082

		host.vm.provider "virtualbox" do |vb|
			# Customize the amount of memory on the VM:
			vb.memory = 512
			vb.cpus = 2
		end

	end


	config.vm.define "ubuntu16.04" do |host|

		host.vm.box = "bento/ubuntu-16.04"

		#
		# Stick with the default insecure key so that we can Ansible to 
		# configure this instance.
		#
		host.ssh.insert_key = false

		#
		# Cache packages we download on the host machine
		#
		if Vagrant.has_plugin?("vagrant-cachier")
			host.cache.scope = :box
		end

		#
		# Disable updating the guest extensions because this is usually 
		# more trouble than it's worth.
		#
		if Vagrant.has_plugin?("vagrant-vbguest")
			host.vbguest.auto_update = false
		end

		host.vm.network "forwarded_port", guest: 80, host: 8081

		host.vm.provider "virtualbox" do |vb|
			# Customize the amount of memory on the VM:
			vb.memory = 512
			vb.cpus = 2

			#
			# Put this in to avoid waiting 5 minutes on
			# the "A start job is running for raise network interfaces" 
			# line on the console.
			#
			vb.customize ["modifyvm", :id, "--cableconnected1", "on"]

		end

	end

end


