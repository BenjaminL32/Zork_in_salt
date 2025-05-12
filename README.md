# Zork in salt
How to run the classic text-based adventure game Zork using Salt.  
The scope of this project is to get Zork and dependencies installed in to a virtual machine using Salt.  
# Walktrough guide.  
1. Install VirtualBox on your machine from https://www.virtualbox.org/wiki/Downloads (Other virtualization enviroments should work but require changes to the Vagrantfile.)  
2. Install the proper version of vagrant on your desired machine from https://developer.hashicorp.com/vagrant/install  
3. Make a new directory and save Vagrantfile from this repository on it  
4. Navigate to the new directory on CLI and give the command ``vagrant up`` to start two virtual machines, one master and one slave. ( Might need ``vagrant init debian12/bookworm64`` first)  
5. When machines are up, use the CLI to SSH in to the master-machine with the command `` vagrant ssh master`` (You working directory in CLI should be your project directory)  
6. Once SSH-connection is established, run the init.sls file with the command ``sudo salt '*' state.apply init`` (Command takes about 30 seconds to run). Once the run is complete, exit the master-machine.  
7. Once the run is complete, establish an SSH-connection to the slave machine using command ``vagrant ssh gamer`` (Make sure your current directory is still the same)
8. Change your directory to /home/vagrant/zork_undiscovered with the command `` cd zork_undiscovered``
9. Inside the directory, give the command ``frotz ZTUU.z5`` (Frotz is the z-machine interpreter that runs the game, ZTUU.z5 is the name of the gamefile.)
10. Happy playing :)
   
