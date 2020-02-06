patiant 1    ---->   summary 1

patiant 2    ---->   summary 2

patiant 3    ---->   summary 3

patiant 4    ---->   summary 4


```js
// patient detail with desease
    db.patients.insertOne({
        name: "max",
        age: 29,
        diseaseSummary: "summary-max-1"
    })

// desease in collection
    db.diseaseSummaries.insertOne({
        _id:"summary-max-1",
        disease:["cold", "feaver"]
    })

// merge the data
    db.patients.aggregate([
        {
            $lookup:{
                from: "diseaseSummaries",
                localField: "diseaseSummary",
                foreignField: "_id", 
                as: "diseaseSummary"
            }
        }
    ])
```