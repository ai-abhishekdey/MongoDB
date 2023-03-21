## MongoDB Commands

**Author : Abhishek Dey**

**Last Modified : 21/03/2023**


### Mongo shell

```
mongosh

```

* Output

```

abhishek@abhishek:~$ mongosh
Current Mongosh Log ID:	6419af85bc6b74b057a2527e
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+1.8.0
Using MongoDB:		5.0.15
Using Mongosh:		1.8.0

For mongosh info see: https://docs.mongodb.com/mongodb-shell/

------
   The server generated these startup warnings when booting
   2023-03-21T18:01:59.741+05:30: Using the XFS filesystem is strongly recommended with the WiredTiger storage engine. See http://dochub.mongodb.org/core/prodnotes-filesystem
   2023-03-21T18:02:04.545+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

------
   Enable MongoDB's free cloud-based monitoring service, which will then receive and display
   metrics about your deployment (disk utilization, CPU, operation statistics, etc).
   
   The monitoring data will be available on a MongoDB website with a unique URL accessible to you
   and anyone you share the URL with. MongoDB may use this information to make product
   improvements and to suggest MongoDB products and deployment options to you.
   
   To enable free monitoring, run the following command: db.enableFreeMonitoring()
   To permanently disable this reminder, run the following command: db.disableFreeMonitoring()
------

```

### Show all databases

```
show dbs

```

* Output

```
test> show dbs
admin    40.00 KiB
config  108.00 KiB
local    72.00 KiB
test> 

```

### Create a new database

```
use DATABASE_NAME

```

* Output

```
test> use Employee_database
switched to db Employee_database
Employee_database> 

```

### Know your current selected database

```

db

```

* Output

```
Employee_database> db
Employee_database
Employee_database> 

```

## Note: In MongoDB, "collections" are considered as "tables in mysql"

### Create collections (tables)

```

db.createCollection("COLLECTION_NAME")

```

* Output

```

Employee_database> db.createCollection("Employee_info")
{ ok: 1 }
Employee_database> db.createCollection("Department_info")
{ ok: 1 }
Employee_database> db.createCollection("Management_info")
{ ok: 1 }
Employee_database> 


```

### Show collections

```
show collections

```

* Output

```

Employee_database> show collections
Department_info
Employee_info
Management_info
Employee_database> 

```

### Delete / Drop collection

```

db.COLLECTION_NAME.drop()

```

* Output

```

Employee_database> db.Management_info.drop()
true
Employee_database> show collections
Department_info
Employee_info
Employee_database> 


```

## Note: In MongoDB, entries are saved as "key":"value" pair in JSON format

### Insert single document(entry) in selected collection(table)

```

db.COLLECTION_NAME.insert({"key":"value"})

```

* Output

```

Employee_database> db.Employee_info.insert({"First_Name":"Rakesh","Last_Name":"Agarwal"})
DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
{
  acknowledged: true,
  insertedIds: { '0': ObjectId("6419b57f46e67f7691173fc9") }
}
Employee_database> 

```

## Insert Multiple documents in selected collection


```

db.COLLECTION_NAME.insert([{"key":"value"},{"key":"value"}])

```

* Output

```

Employee_database> db.Employee_info.insert([{"First_Name":"Sachin","Last_Name":"Tendulkar","Age":30},{"First_Name":"Sourav","Last_Name":"Ganguly","Address:":"Kolkata"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("6419b71f46e67f7691173fca"),
    '1': ObjectId("6419b71f46e67f7691173fcb")
  }
}
Employee_database> 

```

## To see all the documents (entries) in the collection

```

db.COLLECTION_NAME.find()

```

* Output

```

Employee_database> db.Employee_info.find()
[
  {
    _id: ObjectId("6419b57f46e67f7691173fc9"),
    First_Name: 'Rakesh',
    Last_Name: 'Agarwal'
  },
  {
    _id: ObjectId("6419b71f46e67f7691173fca"),
    First_Name: 'Sachin',
    Last_Name: 'Tendulkar',
    Age: 30
  },
  {
    _id: ObjectId("6419b71f46e67f7691173fcb"),
    First_Name: 'Sourav',
    Last_Name: 'Ganguly',
    'Address:': 'Kolkata'
  }
]
Employee_database> 


```


## References:

1. https://blog.e-zest.com/basic-commands-for-mongodb

