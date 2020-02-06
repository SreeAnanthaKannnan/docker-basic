## create
    insertOne(data, options)
    insertMany(data, options)
    insert(data, options)

``` js
// create single collection
   db.flightData.insertOne({
      _id:"yoga",
      name:"Yoga"
    })

// create multiple collection
    db.flightData.insertMany([{
            _id:"cooking",
            name:"Cooking"
        },
        {
           _id:"hiking",
           name:"Hiking"
        }
    ])

// if you are try to insert this data, the first object only will insert, other objects are thow the error. because this "hiking" _id is already exist. 

    db.flightData.insertMany([{
            _id:"reading",
            name:"Reading"
        },
        {
           _id:"hiking",
           name:"Hiking"
        }
    ])

// if you want to insert the data with dublicate key, then use "orderd":false

// Basically it's means if any error throw in inserting data, then the next object will be try to insert

    db.flightData.insertMany([{
            _id:"reading",
            name:"Reading"
        },
        {
           _id:"hiking",
           name:"Hiking"
        }
    ],{ ordered: false})

```