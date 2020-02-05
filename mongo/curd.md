## create
    insertOne(data, options)
    insertMany(data, options)

---
## read
    find(filter, options)
    findOne(filter, options)

    db.flightData.find({"departureAirport": "LHR"})
    db.flightData.findOne({"departureAirport": "LHR"})

*It's will find all the data*
  
    db.flightData.find()

*pretty() method used to show the data with alignment in the mongo shell*

    db.flightData.find().pretty()

*Basically to find method only return TOP20 value, but if you want all data, then you need ot use toArray() or forEach() method*
  
    db.passengers.find().toArray()
    db.passengers.find().forEach((passengerData) => {printjson(passengerData)})


*gt greater then* to find greater then 500 value

    db.flightData.find({"distance": {$gt: 500}})

*get only name form the passenger collection. _id will retrive automatically, if you don't want _id then use secound query as _id:0*

    db.passengers.find({}, {name:1})
    db.passengers.find({}, { _id:0, name:1 })

##### find arry inside data
```js
db.passengers.find({"name":"ananth"})

{ "_id" : ObjectId("5e3a6f784df2d366ba560141"), "name" : "ananth", "age" : 28,"hobbies" : [ "sports", "cooking" ] }
```
   
```js
 db.passengers.find({"hobbies":"cooking"})

{ "_id" : ObjectId("5e3a6f784df2d366ba560141"), "name" : "ananth", "age" : 28, "hobbies" : [ "sports", "cooking" ] }
{ "_id" : ObjectId("5e3a6f784df2d366ba560142"), "name" : "kannan", "age" : 10, "hobbies" : [ "reading", "cooking" ] }
```

```js
    db.passengers.find({"name":"ananth"}).hobbies
    // basiclly this command not working for me
```

##### find object insde object
```js
    db.flightData.find({"status.description":"on-time"})
    // only returns the status inside description value on-time object 
```


---
## update
    update(filter, data, options)
    updateOne(filter, data, options)
    updateMany(filter, data, options)
    replaceOne(filter, data, options)

    db.flightData.updateOne({ "distance": 950}, {$set: {marker: "delete"}})

    db.flightData.updateMany({}, {$set:{marker:"toDelete"}})

*update and replace operations are delete all key and data only repace as marker key and value below query result only _id and marker another data are will be lost*

    db.flightData.update({ "distance": 950}, {marker: "delete"})
    db.flightData.replaceOne({ "distance": 950}, {marker: "delete"})
---
## delete
    deleteOne(filter, options)
    deleteMany(filter, options)

    db.flightData.deleteOne({"departureAirport": "LHR"})
    db.flightData.deleteMany({"departureAirport": "LHR"})
    db.flightData.deleteMany({}) 

