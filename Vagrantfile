$script = <<-SCRIPT
sudo apt update -y && sudo apt upgrade -y
sudo apt install git ansible vim -y
sudo mkdir -p /etc/ansible
sudo echo "debian" >> /etc/ansible/hosts
git clone https://github.com/msouvatdy/diverse-ansible-roles.git 
SCRIPT

Vagrant.configure("2") do |config|
	config.vm.provision "shell", inline: $script
	config.vm.boot_timeout = 1000
	config.vm.define "debian" do |debian|
		debian.vm.box = "bento/debian-11"
		debian.vm.hostname= "debian"
		debian.vm.network "private_network", ip: "10.10.20.222"
		debian.vm.provider "virtualbox" do |v|
			v.memory = 8192
			v.cpus = 2
			v.name = "debian"
		end
	end
end