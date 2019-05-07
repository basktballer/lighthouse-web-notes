#Week 3 Day 4 Notes
## Lecture Notes

* Show a little bit of code
* Have a conversation about important issues associated with full stack
* Talk about databases and Mongo
* End with demo of full application built with Mongo


``` javascript
// Example 1
const  data = {
  users: [
    {name: "Juan", course:'web'},
    {name: "Dave", course: 'ios'}
  ],
  create: create
}

function writingToDisk() {
  console.log("writing to disk...")
}

function loadFromTheDisk() {
  console.log("loading");
}

function create (newUser) {
  loadFromTheDisk();        // load everything to the disk every time before you create
  this.users.push(newUser); // refers to data.users when run from within the data
  writingToDisk();
}

function serach (field, value) {
  return data.users.filter(usr => usr[field] == value)
}

data.create({name: 'bob', course: 'juggling', city: 'Calgary'})
data.create({name: 'dylan', course: 'ios', city: 'Toronto'})

console.log(data)

console.log(search('course', 'ios'))

```
* As more data and users, the data grows
* What happens when we stop running the application? 
* Currently, this way, the data is stored in memory
* If application is running, memory is yours, when stopped, memory is released
* What if we have many users, split traffic to 2 computers
* Don't want 2 separate files to maintain
* Imagine 2 different creates from 2 different machines, both writing to the same file
* Data has to be in one place, no matter how many computers running
* Concurrency problem, any 2 clients to your data
* Load the data every time before writing, as a result the application got more convoluted
* Each time you write, edit
* What if we are writing to disk consistently, then hard drive fails?
* What if data is physically compromised? 
* Write to two places, keep a back up. Slower but data is safe still 

* The world of databases is being obsessive about keeping data safe
* Take all concerns about data and have software for it
* Work with databases. Data bases will do all the data management
* Lots of ways to manage data
* Use FS to write to file, store data in JSON file
* Sometimes JSON file is enough, other times, there are more demanding requirements
  * Many users, many posts
* Lots of solutions out there

### MongoDB

* Imagine if application has access to another application running the database
* MongoDB is a database server, different application running from your application
* Your application will be a client to a database server
* Mongo doesn't care what is there already when putting in new documents in the collection
* ID is a unique identifer, time stamp, rather than random generated, variant of UNIX time code
  * ObjectID("#####")
* mongod is the database server, mongo daemon runs all the time
./mongod [filepath]
* Waiting for application
* ./mongo
  * show dbs
  * use demo
  * show collections
  * db.users.find()
  * db.users.find().pretty()
  * db.users.insert({name: 'bob', course: 'juggling', city: 'Calgary'})
  * db.users.find().pretty()
  * db.users.find({name: "Juan"}) 
  * db.users.find({course: "juggling"}) 
  * db.users.find({"projects.id":"P1"})
  * db.users.find({"_id": ObjectID("###")})
  * db.users.find.limit(1)

* Can also call mongo from javascript application
* Tons of documentation out there, but depends on what actually doing to figure it out
* Query an array of embedded or nested elements
* Add specific qualifiers to operator
* Pain to learn about mongo that is unique to it
* But it is efficient for querying Javascript objects and documents
* Server, and server needs to be running and connected before it can work
* Don't worry about performance or saving bytes

* Mongo Example 1
  ``` javascript
  db.users.find(
    { age: { $gt: 18 } },
    { name: 1, address: 1 }     // only return name and address
  ).limit(5)                    // only return the first five, don't assume any order, if needed add it to query

  ```

* Mongo Example 2
  * use todos
  * show collections
  * db.todos.find()
   
  db.collection("todos").find().toArray((err, results) => {
    const templateVars = {
      todos: results
    };
    if (!err)
      res.render("todos/index", templateVars);
    else
      res.status(500).send("DB not responding...")
  })

* Submit something to server from a form, stored in server as an object
* Write to mongo and replicate to all servers
* insertOne
* mongoDB is a library, know how to talk to the server library
* not the actual server
* Make sure the driver is installed, if it is it can talk to any mongo db anywhere
* Explicitly specify protocol, location, database
* First need to connect
* Make sure your connect happens at beginning of application and stays open
  * Returns a mongoInstance, set it to variable db
  * Ensure that mongo is connection established before query
* 
