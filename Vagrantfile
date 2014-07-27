#!/usr/bin/env ruby

Vagrant.require_version '>=1.6.0'

Vagrant.configure("2") do |config|
	
	# box options, cpu/mem
	config.vm.provider :virtualbox do |virtualbox|
		host = RbConfig::CONFIG['host_os']
		
		# Give VM 1/4 system memory & access to all cpu cores on the host
		if host =~ /darwin/
			cpus = `sysctl -n hw.ncpu`.to_i
			# sysctl returns Bytes and we need to convert to MB
			mem = `sysctl -n hw.memsize`.to_i / 1024 / 1024 / 4
		elsif host =~ /linux/
			cpus = `nproc`.to_i
			# meminfo shows KB and we need to convert to MB
			mem = `grep 'MemTotal' /proc/meminfo | sed -e 's/MemTotal://' -e 's/ kB//'`.to_i / 1024 / 4
		else # sorry Windows folks, I can't help you
			cpus = 2
			mem = 1024
		end

		virtualbox.customize ["modifyvm", :id, "--memory", mem]
		virtualbox.customize ["modifyvm", :id, "--cpus", cpus]
    end
    
    # manage hostname
	config.hostmanager.enabled = true
	config.hostmanager.manage_host = true
    
    # devbox
    config.vm.define :devbox do |node|
        
        # box
        node.vm.box = "Ubuntu_14.04_LTS"
        node.vm.box_url = 'https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'
        
        # set hostname
        node.vm.hostname = "mybox.dev"
        node.vm.post_up_message = "Run: vagrant ssh\nand after: ./myproject-local/run.sh"
        
        # network
        node.vm.network :private_network, ip: "192.168.111.180"
        # ssh
        node.vm.network :forwarded_port, guest: 22, host: 2280
        # http
        #node.vm.network :forwarded_port, guest: 8000, host: 8000
        # email
        #node.vm.network :forwarded_port, guest: 1080, host: 1080
    end
    
    # provisioning
    #config.vm.provision :ansible do |ansible|
    #    ansible.playbook = "deployment/ansible/playbook/vagrant.yml"
    #    ansible.inventory_path = "deployment/ansible/inventory/vagrant"
    #    ansible.verbose = "v"
    #    ansible.limit = 'all'
    #end
    #
end
