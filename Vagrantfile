$script = <<-SCRIPT
sudo apt update -y
sudo apt install git ansible vim -y
sudo mkdir -p /etc/ansible
sudo echo "debian" >> /etc/ansible/hosts
git clone https://github.com/msouvatdy/diverse-ansible-roles.git

mkdir /home/vagrant/.ssh
echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDalwOSFcijdV9DSm30ukXPgk7BHkphlBldOkluDf5YcYg489cZdibOeySribIGdMS/0omLmxgvmhQ+xIl6cX2cSQAJz0WJrl/SieW9aeWxeH0t7cG6AssstHOX/N93NRFPNNCepmkzNLqwiY4W8UwKxOBmOtf4HP66PrYDd0FwfOKlO3G/6lUaeA83ZbTYhMHiuo2aIrl+rApQZeFuvjPtPfsLA6/yGfRIpNLUP97PXyFROLgba/PhD/pPusFRlioHD7GcUIzu/QMk9d1wSkqzdLP/hU38k0CxEyQCHJTT3PEZz6ciLpyAtO74bi9WT+fLg2GsgFEbHARb8XD7i7FrYHFsqEq9OpxChq24WgN6UYaRzqO/xCN2MhYPoswyQOy1p8qZjzo4gEKRt7q0RwFcCNJGgGXrEBjp6VSY5Id4tvdYx+hJNi6RPrD0dwmCBoYW34HGVdzKIbh6mts1PYmj+1Xdm62FGXzLKtXRqZ9oMA2jkLrX3X3h1iSaWu4Jl58= vagrant@debian" >> /home/vagrant/.ssh/authorized_keys

echo "-----BEGIN OPENSSH PRIVATE KEY-----
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
-----END OPENSSH PRIVATE KEY-----
" > /home/vagrant/.ssh/id_rsa

chmod 600 /home/vagrant/.ssh/id_rsa
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