# -*- mode: ruby -*-
# vi: set ft=ruby :

$master = <<-MASTER
set -o verbose
sudo apt-get update
sudo apt-get install -y curl tree
sudo mkdir -p /srv/salt
sudo curl -o /srv/salt/init.sls https://raw.githubusercontent.com/BenjaminL32/Zork_in_salt/refs/heads/main/init.sls
sudo mkdir -p /etc/apt/keyrings
sudo curl -fsSL https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public | sudo tee /etc/apt/keyrings/salt-archive-keyring.pgp
sudo curl -fsSL https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources | sudo tee /etc/apt/sources.list.d/salt.sources
sudo apt-get update
sudo apt-get install -y salt-master
sudo systemctl restart salt-master
sudo apt-get update
MASTER

$minion = <<-MINION
set -o verbose
sudo apt-get update
sudo apt-get install -y curl tree
sudo mkdir -p /etc/apt/keyrings
sudo curl -fsSL https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public | sudo tee /etc/apt/keyrings/salt-archive-keyring.pgp
sudo curl -fsSL https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources | sudo tee /etc/apt/sources.list.d/salt.sources
sudo apt-get update
sudo apt-get install -y salt-minion
echo -e 'master: 192.168.88.101' |sudo tee /etc/salt/minion
sudo systemctl restart salt-minion
sudo apt-get update
MINION


Vagrant.configure("2") do |config|
  
  config.vm.box = "debian/bookworm64"

	config.vm.define "master" do |master|
		master.vm.hostname = "master"
		master.vm.network "private_network", ip: "192.168.88.101"
		master.vm.provision "shell", inline: $master
	end

	config.vm.define "gamer", primary: true do |gamer|
		gamer.vm.hostname = "gamer"
		gamer.vm.network "private_network", ip: "192.168.88.102"
		gamer.vm.provision "shell", inline: $minion
	 end
end
