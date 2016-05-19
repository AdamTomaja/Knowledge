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
* Create new collection explicitly
```javascript
db.createCollection("newCollection");
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

# Create user and enable authorization #
* First of all You should create some database. To do this, insert some document into collection and db will be created automatically.
```javascript
use myDb
db.myCollection.insert({""});
```
* Now You can create new User with password and roles. New user with name "adam" and password "veryComplexPassword" will be created. This user will be able to read and modify "myDb" database
```javascript
db.createUser({user: "adam", pwd: "veryComplexPassword", roles: ["readWrite"]});
```
* Set *security.authorization* property to *enabled*. You can do this in /etc/mongod.conf file
* Restart service
```bash
service mongod restart
```
* Connect to database by the client and type
```javascript
use myDb
db.auth("adam", "veryComplexPassword");
```
* Now You should be authorized to do some operations on database

# Graphical management tool for MongoDB
* https://robomongo.org/download

# Great Java library, simple queries and mapping to POJO
* http://jongo.org

# Creating new server functions and using them #
* Create new function
```javascript
db.system.js.save({
     _id: "echo", 
     value: function(text){
               print(text);
           }
});
```
* Load function from database
```javascript
db.loadServerScripts();
```
* Now You can use the function
```javascript
echo("Hello world!");
```
