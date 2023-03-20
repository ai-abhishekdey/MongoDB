## Mongodb Installation in Ubuntu 22.04

---

### Install the dependencies

```
sudo apt update

sudo apt install dirmngr gnupg apt-transport-https ca-certificates software-properties-common

```

### Add MongoDB GPG Key

```

wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -

```

### Create a list for MongoDB and libssl1.1

```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list

```

```

echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list

```

* Update the local package database

```
sudo apt-get update

sudo apt-get install libssl1.1

```

### Install the MongoDB 

```

sudo apt-get install -y mongodb-org

```

### Start the MongoDB service and enable it to start automatically after rebooting the system

```

systemctl start mongod

systemctl enable mongod

```

### check the status of the MongoDB service


```
systemctl status mongod

```

* Output

```
abhishek@abhishek:~$ systemctl status mongod
● mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-03-20 21:06:23 IST; 2min 36s ago
       Docs: https://docs.mongodb.org/manual
   Main PID: 16893 (mongod)
     Memory: 64.6M
        CPU: 2.368s
     CGroup: /system.slice/mongod.service
             └─16893 /usr/bin/mongod --config /etc/mongod.conf

Mar 20 21:06:23 abhishek systemd[1]: Started MongoDB Database Server.
abhishek@abhishek:~$ 

```


### Accessing MongoDB shell

```
mongo

```

* Output

```
MongoDB shell version v5.0.15
connecting to: mongodb://127.0.0.1:27017/?compressors=disabled&gssapiServiceName=mongodb
Implicit session: session { "id" : UUID("f3a5fbb0-f1c8-467b-a122-066c392c987e") }
MongoDB server version: 5.0.15
================
Warning: the "mongo" shell has been superseded by "mongosh",
which delivers improved usability and compatibility.The "mongo" shell has been deprecated and will be removed in
an upcoming release.
For installation instructions, see
https://docs.mongodb.com/mongodb-shell/install/
================
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
	https://docs.mongodb.com/
Questions? Try the MongoDB Developer Community Forums
	https://community.mongodb.com
---
The server generated these startup warnings when booting: 
        2023-03-20T21:06:24.446+05:30: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
        2023-03-20T21:06:26.176+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
---
---
        Enable MongoDB's free cloud-based monitoring service, which will then receive and display
        metrics about your deployment (disk utilization, CPU, operation statistics, etc).

        The monitoring data will be available on a MongoDB website with a unique URL accessible to you
        and anyone you share the URL with. MongoDB may use this information to make product
        improvements and to suggest MongoDB products and deployment options to you.

        To enable free monitoring, run the following command: db.enableFreeMonitoring()
        To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
---
> 



```

## References:

1. https://wiki.crowncloud.net/?How_to_Install_Latest_MongoDB_on_Ubuntu_22_04

2. https://www.youtube.com/watch?v=HhfnuGcB3wc
