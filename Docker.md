# Basic commands
* ```docker pull ubuntu```	pull ubuntu image from online docker hub
* ```docker run -i -t ubuntu bash```	run ubuntu image in interactive mode and call bash process
* ```docker commit hungry_archimedes``` apache	save 'hungry_archimedes' container state to 'apache' image
* ```docker run -p 80:80 -i -t apache bash```run ubuntu image in interactive mode, call bash process, and forward port 80 from the container to the port 80 of host vm
* **ctrl + p -> ctrl + q**	detach from running interactive container
* ```docker attach hungry_archimedes```	attach to running container
* ```docker stop $(docker ps -a -q)```	stop all containers
* ```docker rm $(docker ps -a -q)```	remove all containers
* 
# Other usefull parameters
* ```-v /host:/guest``` - Mount /host directory of host to the /guest directory in container
