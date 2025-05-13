# Zork in salt
How to run the classic text-based adventure game Zork using Salt.  
The scope of this project is to get Zork and dependencies installed in to a virtual machine using Salt.  
# Walktrough guide.  
1. Install VirtualBox on your machine from https://www.virtualbox.org/wiki/Downloads (Other virtualization enviroments should work but require changes to the Vagrantfile.)  
2. Install the proper version of vagrant on your desired machine from https://developer.hashicorp.com/vagrant/install
3. Install the right operating system box on vagrant with the command ``vagrant box add debian/bookworm64``  
4. Make a new directory and save Vagrantfile from this repository on it (You can download it straight from github using the download button, copy-pasting the data in to file named "Vagrantfile", using ``-curl -o https://github.com/BenjaminL32/Zork_in_salt/blob/main/Vagrantfile``, what way works best for you.  
5. Navigate to the new directory on CLI with the command `` cd /yourprojektfile`` and give the command ``vagrant up`` to start two virtual machines, one master and one slave. ( Might need ``vagrant init debian12/bookworm64`` first)  
6. When machines are up, use the CLI to SSH in to the master-machine with the command `` vagrant ssh master`` (You working directory in CLI should be your project directory)
7. Once SSH-connection is established, accept minion keys with the command `` sudo salt-key -A``  
8. Now run the init.sls file with the command ``sudo salt '*' state.apply init`` (Command takes about 30 seconds to run). Once the run is complete, exit the master-machine.  
9. Once the run is complete, establish an SSH-connection to the slave machine using command ``vagrant ssh gamer`` (Make sure your current directory is still the same)
10. Change your directory to /home/vagrant/zork_undiscovered with the command `` cd zork_undiscovered``
11. Inside the directory, give the command ``frotz ZTUU.z5`` (Frotz is the z-machine interpreter that runs the game, ZTUU.z5 is the name of the gamefile.)
12. Happy playing :)
   
