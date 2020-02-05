#### create
    insertOne(data, options)
    insertMany(data, options)

---
#### read
    find(filter, options)
    findOne(filter, options)

---
## update
    updateOne(filter, data, options)
    updateMany(filter, data, options)
    replaceOne(filter, data, options)

    db.flighData.updateOne({ "distance": 950}, {$set: {marker: "delete"}})

---
## delete
    deleteOne(filter, options)
    deleteMany(filter, options)

    db.flighData.deleteOne({"departureAirport": "LHR"})
    db.flighData.deleteOne({"departureAirport": "LHR"})
