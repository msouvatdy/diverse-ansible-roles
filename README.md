# Diverse-ansible-roles

This is a random project.
All roles have been tested on debian 11 for the moment.

## What kind of roles ?

In each role folder, there is a README that explain all variables used by the role and how to use it.

> **Note:** Some roles are not developed or fully developed yet.

| Role | Purpose of the role|
|----------------|-------------------------------|
| docker | install docker |
| gitlab | install gitlab using ansible helm module|
| helm   | install helm binary  |
| kubeadm | install containerd and kubeadm|
| nfs   | install a nfs server|
| rancher | install rancher using ansible helm module|
| storage-class-nfs | install storage class and csi-storage-nfs via ansible helm module|
| traefik-ingress| install ingress controller Traefik using ansible helm module|

## Test the project

### Creating the environment

In order to test all my ansible roles, here is how I setup my environment.
First, I am using VirtualBox in version 7.0.6 r155176 and vagrant in version 2.3.4 .

Here is my Vagrantfile

```bash
Vagrant.configure("2") do |config|
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
```

### Configure the environment

In SSH on the debian machine, here is all commands I used to setup my environment:

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install git ansible vim -y
sudo mkdir -p /etc/ansible
sudo echo "debian" >> /etc/ansible/hosts
git clone https://github.com/msouvatdy/diverse-ansible-roles.git
ssh-keygen
#all answer by default
ssh-copy-id vagrant@debian
#default password of the user vagrant is vagrant
```