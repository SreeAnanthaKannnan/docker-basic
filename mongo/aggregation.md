### Aggregation

#### Group
```js
// find how many female live in every location 
db.persons.aggregate([
    { $match: { gender: 'female'}},
    { $group: { _id: { place: "$location.state" }, totalPersons: {$sum: 1}  } }
])

// find how many female live in "ankara" location
db.persons.aggregate([
    { $match: { gender: 'female', 'location.state': 'ankara'}},
    { $group: { _id: { place: "$location.state" }, totalPersons: {$sum: 1}  } }
])

```

#### sort
```js
// sort desending order
db.persons.aggregate([
    { $match: { gender: 'female'}},
    { $group: { _id: { place: "$location.state" }, totalPersons: {$sum: 1}  } },
    { $sort: { totalPersons: -1 }}
]) 
```

#### project
##### need to study project
```js
// get firstname and last name as a full name
db.persons.aggregate([
    { 
        $project: { 
            _id:0, 
            gender:1, 
            fullName: { $concat: ["$name.first", " ", "$name.last"] } 
        }
    }
])

```

#### pushing element into newly created array
```js
db.persons.aggregate([
    { $group: {_id: { age: '$age' } } }
])
```