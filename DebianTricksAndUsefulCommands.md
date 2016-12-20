# Show files opened by process
```bash
lsof -p <pid>
```
# Install VirtualBox guest additions 
* Login as a root 
```bash
su
```
* Update apt database, and upgrade packages 
```bash
apt-get update
apt-get upgrade
```
* Install required packages
```bash
apt-get install build-essential module-assistant
```
* Configure your system for building kernel modules 
```bash
m-a prepare
```
* Mount guest additions cd by selecting the *Install Guest Additions* from *Devices* menu
* Execute install script
```bash
sh /media/cdrom/VBoxLinuxAdditions.run
```
# Add user to virtual box group to get shared-folder permissions
```bash
sudo adduser your-user vboxsf
```

# How do I compress and extract the whole directory ?
* **Compress**: ```tar -zcvf archive-name.tar.gz directory-name```
* **Decompress**: ```tar -zxvf archive.tar.gz -C /outputDirectory```

# Install Java
* Download JDK ```wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u5-b13/jdk-8u5-linux-x64.tar.gz```
* Decompress archive ```tar -zxf jdk-8u5-linux-x64.tar.gz -C /opt/jdk```
* Add JAVA alternative ```update-alternatives --install /usr/bin/java java /opt/jdk/jdk1.8.0_05/bin/java 100```
* Add JAVAC alternative ```update-alternatives --install /usr/bin/javac javac /opt/jdk/jdk1.8.0_05/bin/javac 100```
* Verify alternatives ```update-alternatives --display java```

# Change version of java
* Enter the command ```update-alternatives --config java```
* Select desirect application version by number

# Analyze disk space usage
* Install the ncdu application ```apt-get install ncdu`
* Execute analyzer ```ncdu -x -q```

# Analyze disk space usage without ncdu
```bash
du -h / | grep '[0-9\.]\+G'
```
This will show directories with size in gigabytes

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

# Service Script
Create the init script in /etc/init.d/tomcat7 with the contents as per below (your script should work too but I think this one adheres more closely to the standards).

This way Tomcat will start only after network interfaces have been configured.

Init script contents:
```bash
#!/bin/bash

### BEGIN INIT INFO
# Provides:        tomcat7
# Required-Start:  $network
# Required-Stop:   $network
# Default-Start:   2 3 4 5
# Default-Stop:    0 1 6
# Short-Description: Start/Stop Tomcat server
### END INIT INFO

PATH=/sbin:/bin:/usr/sbin:/usr/bin

start() {
 sh /usr/share/tomcat7/bin/startup.sh
}*

stop() {
 sh /usr/share/tomcat7/bin/shutdown.sh
}

case $1 in
  start|stop) $1;;
  restart) stop; start;;
  *) echo "Run as $0 <start|stop|restart>"; exit 1;;
esac
```
Change its permissions and add the correct symlinks automatically:

```bash
chmod 755 /etc/init.d/tomcat7
update-rc.d tomcat7 defaults
```

And from now on it will be automatically started and shut down upon entering the appropriate runlevels. You can also control it with
```bash
service tomcat7 <stop|start|restart>
```

