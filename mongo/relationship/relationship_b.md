#### blog

__user__

    name
    age
    email

__post__
    title
    text
    tag
__command__

---
```js
// insert users
    db.user.insertMany([
        {
            name:"ananth",
            age: 20,
            email: "ananth@gmail.com"
        },
        {
            name:"sree",
            age: 15,
            email: "sree@gmail.com"
        }
    ])
// insert posts
    db.posts.insertMany([
        {
            title:"my first post",
            text: "this is my my first post. hope you like it",
            tags: ["new", "tech"],
            creator:ObjectId("5e3ba7604340af13cc9f1c2f"),
            comments: [
                {
                    text:"I like thid post..",
                    author: ObjectId("5e3ba7604340af13cc9f1c30")
                }
            ]
        }
    ])
```

#### schema creation
```js
    db.createCollection('posts', {
        validator:{
            $jsonSchema:{
                bsonType:'object',
                required:['title', 'text', 'creator', 'comments'],
                properties:{
                    title:{
                        bsonType: "string",
                        description: "must be string"
                    },
                    text:{
                        bsonType: "string",
                        description: "must be string"
                    },
                    creator:{
                        bsonType: "objectId",
                        description: "must be an objectId"
                    },
                    comments:{
                        bsonType: "array",
                        description: "must be an array",
                        items:{
                            bsonType: "object",
                            required:["text", "author"],
                            properties:{
                                text:{
                                bsonType:"string",
                                description: "must be string"
                                },
                                author:{
                                    bsonType:"objectId",
                                    description:"must be object"
                                }
                            }
                        }
                    }
                }
            }
        },
    // validationAction: "warn"
    })
// predefine validationAction is error
// if the validation action error means, you can't able to insert the worng validation data.
// if the validation action warn means, you can enter the data with warnign 
```