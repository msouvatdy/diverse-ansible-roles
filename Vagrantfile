Vagrant.configure("2") do |config|
	config.vm.boot_timeout = 1000
	config.vm.define "rancher" do |rancher|
		rancher.vm.box = "bento/debian-11"
		rancher.vm.hostname= "rancher"
		rancher.vm.network "private_network", ip: "10.10.20.222"
		rancher.vm.provider "virtualbox" do |v|
			v.memory = 8192
			v.cpus = 2
			v.name = "rancher"
		end
	end
end