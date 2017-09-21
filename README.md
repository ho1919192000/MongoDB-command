# MongoDB-command
MongoDB basic command
## MongoDB
MongoDB: None-SQL
Save data in database without table
- mongod.exe => database
- mongo.exe => command line
## Setting Environment
1. `C:\>cd Program Files\MongoDB\Server\3.4\bin`
=> Cd to the bin directory

2. `C:\Program Files\MongoDB\Server\3.4\bin>mongod`
=> Run mongod

3. `C:\Program Files\MongoDB\Server\3.4\bin>mkdir \data\db`
=> Create a directory for mongoDB to store data

### Command shortcut setting:
Computer Properities => Advanced system seting => Environment Variables
=> New => PATH + "C:\Program Files\MongoDB\Server\3.4\bin"

**Double quote is necessary!!

`C:\Users\Howard>mongod` => Run database
`C:\Users\Howard>mongo` => Connect database

## Set Up for JetBrains IDE's

1. Go to setting => Plugin => add Mongo plugin
2. Go to Mongo explore => set up "Path of mongo shell"
3. Add mongo server => Label: `Localhost` => Click OK
4. Open cmd => `C:\Program Files\MongoDB\Server\3.4\bin>mongod` => Start Server
5. Open Mongo Shell => `db`

## MongoDB Tutorial for Beginners - 3 - Creating Databases and Inserting Data
Create database:

`> use hockey` => If you don't have hockey database, then create one.

`> db` => check what database is using

`> show dbs` => check the list of available databases

`> db.dropDatabase()` => delete a db

### How to add data? it need to go a group of collection

`> db.players.insert(
 {  
         "position":"Right Wing",
         "id":8465166,
         "weight":200,
         "height":"6' 0\"",
         "imageUrl":"http://1.cdn.nhle.com/photos/mugs/8465166.jpg",
         "birthplace":"Seria, BRN",
         "age":37,
         "name":"Craig Adams",
         "birthdate":"April 26, 1977",
         "number":27
      }
)`

Now, we have one collection called players and one document (which is what we just inserted)

### Add MORE than one data

`> db.players.insert([{},{},{}])` => Put the data inside []

`> show collections` => See what collection inside this database

`> db.players.find()` => See what data inside players collection

`> db.players.find().pretty()` => to see the formatted data

`> db.players.findOne()` => Get the first data in the database

`"_id" : ObjectId("59c330bb28b7a72d67f1ad1a")` is the unique id for each data

## Updating, Removing, and Collections

### Remove: `db.players.remove({id})` => {} is called "selection criteria"

`> db.players.remove(
 {"_id" : ObjectId("59c330bb28b7a72d67f1ad1a")}
)`

### Update: ` db.players.update({id},{new object})`

`>  db.players.update(
         {"_id" : ObjectId("59c331ef28b7a72d67f1ad1b")},
         {  
                  "position":"Left Wing",
                  "id":8475761,
                  "weight":195,
                  "height":"6' 2\"",
                  "imageUrl":"http://1.cdn.nhle.com/photos/mugs/8475761.jpg",
                  "birthplace":"Gardena, CA, USA",
                  "age":23,
                  "name":"Bob Bennett",
                  "birthdate":"November 27, 1991",
                  "number":19
           }
)`

### Delete Whole collection

`>  db.players.drop()` => Delete entire collection

## Find and Search Query
`db.players.find({})` =>put selection criteria

`> db.players.find(
     {"position":"Goalie"}
)`

`> db.players.findOne(
{"position":"Goalie"}
)`
=> Only find one

### Mutiple selection criteria
`db.players.find({first_criteria, second_criteria, ets.})`

`> db.players.find(
{"position":"Defenseman", "age":21}
)`

### OR operatior
`db.players.find({$or:[first_criteria, second_criteria, ets...]})`

`> db.players.find(
  {
        $or:[
            {"position":"Left Wing"},
            {"position":"Right Wing"}
        ]
  }
)`

### Condition
`db.players.find({"age": {$gt: number}})` => $gt means greater than $lt lower than

`db.players.find(
      {"age": {$gt:30}}
)`

`$gt => ">"
$lt => "<"
$gte => ">="
$lte => "<="
$ne => "!="`

### Return certain data
`db.players.find({criteria},{which data want to be displayed})` => 1 means "true", 0 means "false"

`db.players.find(
      {"position": "Center"},
      {"name":1, _id:0}
)`
