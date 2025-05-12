# Zork in salt
How to run the classic text-based adventure game Zork using Salt.  
The scope of this project is to get Zork and dependencies installed in to a virtual machine using Salt.  
# Walktrough guide.  
1. Install VirtualBox on your machine from https://www.virtualbox.org/wiki/Downloads (Other virtualization enviroments should work but require changes to the Vagrantfile.)  
2. Install the proper version of vagrant on your desired machine from https://developer.hashicorp.com/vagrant/install  
3. Make a new directory and save Vagrantfile from this repository on it
4. Navigate to the new directory on CLI and give the command ``vagrant up`` to start two virtual machines, one master and one slave. ( Might need ``vagrant init debian12/bookworm64`` first
