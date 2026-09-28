Vagrant.configure("2") do |config|
	
	# Máquina 1: Servidor
	config.vm.define "servidor" do |m1|
		m1.vm.box = "ubuntu/jammy64"
		m1.vm.network "private_network",
			ip: "192.168.56.10"

		
		m1.vm.provider "virtualbox" do |vb|
			vb.memory = 2048
			vb.cpus = 1
		end
	
		# Provisioning
		m1.vm.provision "shell",
			path: "provisioning.sh"
	
		# Arrancar Docker Compose al finalizar
		m1.vm.provision "shell",
			inline: "cd /vagrant && docker-compose up -d"
	end

	# Máquina 2: Cliente
	config.vm.define "cliente" do |m2|
		m2.vm.box = "ubuntu/jammy64"
		m2.vm.network "private_network",
			ip: "192.168.56.20"

		m2.vm.provider "virtualbox" do |vb|
			vb.memory = 1024
			vb.cpus = 1
		end
	end

end