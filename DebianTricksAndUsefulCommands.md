# How do I compress and extract the whole directory ?
* **Compress**: ```tar -zcvf archive-name.tar.gz directory-name```
* **Decompress**: ```tar -zxvf archive.tar.gz -C /outputDirectory```

# Change version of java
* Enter the command ```update-alternatives --config java```
* Select desirect application version by number

# Analyze disk space usage
* Install the ncdu application ```apt-get install ncdu`
* Execute analyzer ```ncdu -x -q```

# Background jobs - screen 
* Install **screen** ```apt-get install screen```
* Start new session ```screen -S mysession```
* Detach from sesssion by **ctrl + a, ctrl + d**
* Display sessions ```screen -list```
* Attach to existing session ```screen -r mysession```

# Networking 
* Release ip address on **eth0** ```dhclient -r eth0```
* Fetch ip address from dhcp on **eth0** interface ```dhclient eth0```
* To make above commands more verbose You can add ```-v``` flag
