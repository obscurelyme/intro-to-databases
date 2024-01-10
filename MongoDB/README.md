# MongoDB

Use with [MongoDB Guide](https://btholt.github.io/complete-intro-to-databases/mongodb)

To get started with MongoDB

```sh
docker run --name test-mongo -dit -p 27017:27017 --rm mongo:4.4.1
```

To access the mongo database we run

```sh
docker exec -it [CONTAINER_NAME] mongo
```

Note that we use the `mongo` command

To show the databases we have run

```sh
show dbs
```

and to make a new datase we run

```sh
use [DATABASE_NAME]
```

to insert into the database we can work with mongo the same way we work with javascript objects.

```js
db.pets.insertOne({ ... })
```

Mongo has the concept called Databases and Collections. A Database can have multiple Collections. In the prior line of code we created a `pets` collection.

### Query Operators

```
$gt - greater than
$gte - greater than or equal to
$lt - less than
$lte - less than or equal to
$eq - equals (usually not necessary)
$ne - not equals
$in - has the value in the array (MongoDB can store arrays and objects too!)
$nin - does not have the value in the array
```

Examples:

Query that finds the number of pets of type `cat` with an age greater than or equal to `12`

```sh
db.pets.count({type: "cat", age: { $gte: 12 }})
```

### Logical Operators

```
$and - Logical &&
$or - Logical ||
$nor
$not - Logical !==
```

```sh
db.pets.count({
  type: "bird",
  $and: [
    { age: {  $gte: 4 } },
    { age: { $lte: 8 } }
  ]
})
```
