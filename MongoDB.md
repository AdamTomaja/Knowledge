# Install Mongo DB on Ubuntu 14.04 #
* Installation 
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```
* MongoDB daemon management
```bash
service mongod start
service mongod restart
service mongd stop
```
* Default data directory on ubuntu 14.04 
```
/var/lib/mongodb/
```

# Basic MongoDB shell commands #
* Show some help
```
help
```

* Display current database
```
db
```

* Show existing databases
``` 
show dbs
```

* Select database You want to use
```
use myDatabase
```

* Create new collection if not exists and insert new document
```
db.myCollection.insert({'Key1': 'Value1', 'Key2': 'Value2'});
```

* Show existing collections
```
show collections
```

* Display server status
```
db.serverStatus()
```

* Official MongoDB shell reference https://docs.mongodb.com/manual/reference/mongo-shell/

