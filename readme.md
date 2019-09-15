![](mongodb.png)

#	MongoDB

*	MongoDB is a No SQL database.
*	MongoDB is written in C++.
*	MongoDB is a NoSQL database system which stores data in the form of BSON documents.
*	mongodb is the native driver for interacting with a mongodb instance and mongoose 
	is an Object modeling tool for MongoDB.
*	BOSCH , MetLife , CISCO, sprinklr
*	more scalable and provide superior performance.
*	Developed in 2000s.
*	Open-source.
*	check MongoDB version => mongod --version  OR  in mongo console db.version()
*	if you want "shard" then then you must do some index
*	Large volumes of rapidly changing structured, semi-structured, and unstructured data
*	If a database does not exist, MongoDB creates the database when you first store data for that database.
*	If a collection does not exist, MongoDB creates the collection when you first store data for that collection.
*	MongoDB supports query operations on geospatial data
*	MongoDB Indexes support the efficient execution of queries in MongoDB. Without indexes, 
	MongoDB must perform a collection scan, i.e. scan every document in a collection, to 
	select those documents that match the query statement. If an appropriate index exists for 
	a query, MongoDB can use the index to limit the number of documents it must inspect.

	
##	Explain the structure of ObjectID in MongoDB.
*	ObjectID is a 12-byte BSON type. These are:
*	4 bytes value representing seconds
*	3 byte machine identifier
*	2 byte process id
*	3 byte counter

##	NoSQL Database Types
*	Document databases -> Documents can contain many different key-value pairs, or key-array pairs, or even nested documents. =>MongoDB
*	Graph stores -> used to store information about networks of data, such as social connections. => Neo4J
*	Key-value stores => Every single item in the database is stored as an attribute name (or 'key'), together with its value.  => Redis
*	Wide-column stores => store columns of data together, instead of rows. =>  Cassandra

##	advantage of MongoDB
*	It supports replica sets
*	It also provides ACID properties at the document level as in the case of relational databases.
*	faster performance = fire and forget inserts to MongoDB, 
*	lower performance = wait til insert has been replicated to multiple nodes before returning

##	Performance advantage :
*	The document model
*	Optional strict consistent level : 
=>	By default, the insertions operation in MongoDB is fire-and-forget, its OK for low value data like logging 
	or click statistical and you want gain more performance. 
	MongoDB also supports "safe mode" which ensure the insertion complete successfully.
*	Flexible Schema :
=>	there is no schema in MongoDB, the document can have any number of fields, 
	the fields can be add to existing document at anytime, dynamically. 
=>	No ALTER TABLE, no rebuild indexing.
=>	The documents are just like Javascript JSON, PHP arrays,


##	disadvantages of MongoDB
*	Data size in MongoDB is typically higher due to e.g. each document has field names stored it
*	no support for transactions - certain atomic operations are supported, at a single document level
*	RAM limitation : 
=>	MongoDB uses memory mapped file, let the Operating System handle the caching. 
=>	The size of you database is limited by virtual memory provided by Operating System and hardware.
=>	don't save serious data into MongoDB. When the data exceed the capacity, your insertions may fails without any warnings!
*	Not support join operation :
*	Not support transaction : 

##	mongodb namespace
*	The MongoDB.Bson top level namespace and its child namespaces contain the classes for managing BSON data. 
*	The top level MongoDB.Bson namespace contains the classes that represent all the basic BSON Types.
*	It contains the classes needed for most interactions with the database.

##	When do we use Namespace in MongoDB?
*	During sequencing of the names of the database and collection name Namespace is used.

##	Define the namespace in mongodb?
*	It is the concatenation of collection name and database.

##	Normalization and denormalization with MongoDB
*	Normalization means reference data with foreign key or references, 
*	denormalization means embed the data to the location its being referenced.
*	Normalization makes your data compact, easy to store and easy to achieve consistency 
	but with low query performance and hard to scale horizontally.
*	denormalization provide high performance query but may cause data inconsistency.
*	It depend on the application to choose normalize or denormalize.

##	maximum size of a MongoDB document
*	The maximum BSON document size is 16 megabytes. 
	The maximum document size helps ensure that a single document cannot use excessive amount of RAM or, 
	during transmission, excessive amount of bandwidth. To store documents larger than the maximum size, 
	MongoDB provides the GridFS API.

##  Does MongoDB support transactions?
*	MongoDB does not support multi-document transactions. However, MongoDB does provide atomic operations on a single document.

##	Does MongoDB handle caching?
*	Yes. MongoDB keeps most recently used data in RAM. If you have created indexes for your queries and your working data set fits in RAM, MongoDB serves all queries from memory.

##	What makes MongoDB the best?
*	High performance (HP)
*	High availability (HA)
*	Easy scalability
*	Rich query language
*	Document Oriented

##	Does MongoDB support primary-key, foreign-key relationship
*	No. By Default, MongoDB doesn't support primary key-foreign key relationship.

##	Can you achieve primary key - foreign key relationships in MongoDB?
*	We can achieve primary key-foreign key relationship by embedding one document inside another.
	For example: An address document can be embedded inside customer document.

##  How does MongoDB provide consistency?
*	MongoDB uses the reader-writer locks, allowing simultaneous readers to access any supply like 
	a database or any collection. But always offers private access to singles writes.

##  Why is MongoDB not chosen for a 32-bit system?
*	Mongo DB is not considered as a 32-bit system because for running the 32-bit MongoDB, 
	with the server, information and indexes require 2 GB. 
	So only it is not used in 32-bit devices.

##	Why 32 bit version of MongoDB are not preferred ?
*	Because MongoDB uses memory mapped files so when you run a 32-bit build of MongoDB, 
	the total storage size of server is 2 GB. But when you run a 64-bit build of MongoDB,
	this provides virtually unlimited storage size. So 64-bit is preferred over 32-bit.

##	Does MongoDB need a lot of RAM?
*	No. There is no need a lot of RAM to run MongoDB. It can be run even on a small amount 
	of RAM because it dynamically allocates and de-allocates RAM according to the requirement 
	of the processes.

##  What is Aggregation in MongoDB?
*	Aggregations are operations that process data records and return computed results.

##  What is the use journaling?
*	Journaling is used to safe backups in mongodb.

##	What is the use of profiler?
*	Profiler is used to show the performance characteristics of every operation against the database.

##  What is replica set oplog?
*	The oplog records all operations that modify the data in the replica set.

##	What is vertical scaling?
*	Vertical scaling adds more CPU and storage resources to increase capacity.

##	Define horizontal scaling.
*	It divides the data set and distributes the data over multiple servers, or shards.

##  Define Mongodb projection.
*	Projection is used to select only necessary data.It did not select whole data of a document.

##  Define Aggregation Pipeline.
*	It is a framework for performing aggregation tasks.T he pipeline is used to transform the 
	documents into aggregated results.

##	Text Search MongoDB
*	MongoDB supports query operations that perform a text search of string content. To perform text search, MongoDB uses a text index and the $text operator.
*	MongoDB provides text indexes to support text search queries on string content. text indexes can include any field whose value is a string or an array of string elements.
*	To perform text search queries, you must have a text index on your collection. A collection can only have one text search index, but that index can cover multiple fields.

##	How can you see the connection used by Mongos?
*	To see the connection used by Mongos use db_adminCommand (“connPoolStats”);

```js
db.stores.insert(
   [
     { _id: 1, name: "Java Hut", description: "Coffee and cakes" },
     { _id: 2, name: "Burger Buns", description: "Gourmet hamburgers" },
     { _id: 3, name: "Coffee Shop", description: "Just coffee" }
   ]
)
db.stores.createIndex( { name: "text", description: "text" } )
db.stores.find( { $text: { $search: "java coffee shop" } } )
db.stores.find( { $text: { $search: "java \"coffee shop\"" } } )
db.stores.find( { $text: { $search: "java shop -coffee" } } )
db.stores.find(
   { $text: { $search: "java coffee shop" } },
   { score: { $meta: "textScore" } }
).sort( { score: { $meta: "textScore" } } )
```

##	read operations can support views:
```js
db.collection.find()
db.collection.findOne()
db.collection.aggregate()
db.collection.count()
db.collection.distinct()
```

##	MongoDb replication:
*	A replica set in MongoDB is a group of mongod processes that maintain the same data set. 
	Replica sets provide redundancy and high availability, and are the basis for all production 
	deployments.
	
```js
mongod --dbpath /var/www/html/node/mongor/mongod1 --replSet rs-test --oplogSize=64 --port 27017 --smallfiles --fork --logpath /var/lib/mongod1.log
mongod --dbpath /var/www/html/node/mongor/mongod2 --replSet rs-test --oplogSize=64 --port 27018 --smallfiles --fork --logpath /var/lib/mongod2.log
mongod --dbpath /var/www/html/node/mongor/mongod3 --replSet rs-test --oplogSize=64 --port 27019 --smallfiles --fork --logpath /var/lib/mongod3.log
```

##	mongo dump:
```js
mongodump --host localhost --port 3017 --db dbName --username username --password "password" --out /var/www/html/mongodump-2018-11-11
```

## mongo restore:
```js
mongorestore --host localhost --port 27017 --username username --password password --db dbName /var/www/html/mongodump-2018-11-11/dbName
```

## Install MongoDB:
```js
    https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/
	
	sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv       2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
	
	echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
	
	sudo apt-get update
	
	sudo apt-get install -y mongodb-org
	
	sudo service mongod start
	
	nano /etc/mongod.conf
		change bind IP to 0.0.0.0
	
	sudo service mongod restart	
	
	sudo systemctl enable mongod
	
	adding authuntication on mongo
		type mongo
		
		Create Admin User
			use admin
			db.createUser(
			  {
				user: "admin_username",
				pwd: "admin_password",
				roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
			  }
			);
		Create DB user
			use db_name
			db.createUser(
			  {
				user: "any_username",
				pwd: "user_password",
				roles: [ { role: "dbAdmin", db: "db_name" }, { role: "readWrite", db: "db_name" } ]
			  }
			);
	
	enable authorization on mongo conf
		nano /etc/mongod.conf
		uncomment security and add authorization
			security:
			  authorization: enabled
		sudo service mongod restart
```