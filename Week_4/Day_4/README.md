#Week 4 Day 4 Notes
## Lecture Notes

* Objective today is to go through how errors are handled in the application
* Needs to become a part of normal workflow
* Talk about promises today

``` javascript

function Do () {
  try {
    something.run()
    let a = 2 + 3
    throw "Tantrum"
  } catch (err) {
    console.log('Ooops', err)
  }
}

Do()

```
* Most web applications are running 24/7, can't bring application to a halt
* Not dealing with errors
* When to do error checking?
* Anytime we do I/O the risk for errors is high
* Writing to DB might fail
* Throw will cause JS to have an error called "Tantrum"
* Useful to force things to do a certain thing
* Can't use try catch to deal with async scenarios
  * ie. Get requests to server that is waiting for call back

* Build own error handling into my own callback
* That's why we see callbacks have dual output
* Your callback has 2 different exit paths, error and no error
* Every time making async call, need to fork the road
* What if there are many async nested? Lots of potential forks
* A better solution is needed

* Introducing Promises
* Promises were introduced to JS in ES6
* Try Catch, to use promises
* Then back to try catch, back to async calls
* Javascript is single threaded
* Main event looping, have request to send out
* Keep doing stuff while other server gets back, keep a note that 
* Put things on callbacks
* Allow for single thread to do other things while it waits for a callback
* Every time there is an I/O operation, I/O is dealt with by a separate thread
* As many as needed, waiting for I/O to come back
* Not locking up javascript up
* Try to do as much as we can as promises / callbacks
* send al code to another thread
* Await can be doen to a promise.all
* All the things we want to do
* To prepare for what's coming, read release notes for Node 12
* Tell all experimental features, anticipating what will happen with Javascript


``` javascript
const request = require('request');

function promisifiedGet(url) {
  return new Promise((resolve, reject) => {
    //throw "will not finish my promise"
    request.get(url, (err, response) => {
      if (err) {
        reject(err);
      } else {
        resolve(response.body);
      }
    });
  });
}

let p1 = promisifiedGet(url)
let p2 = promiseifiedGet(url2)

// below only executes if promise is good, if not do the .catch
// won't run until promise is resolved
// whatever is rejected is what is sent to catch
// can have 2 promises out, both act independently and try to access server to get results
p1.then((data) => {
  console.log(`First Data is ${data}`);
  return 1; // sends flow to next then
})
.then(id => {
  p2.then((data) => { // can also run promisifiedGet(url2).then -> to launch second promise upon success of first promise
    console.log(`second data is ${data}`);
  })
  .catch(err => {
    console.log("Double wrong inside the .catch", err);
  })
})
.catch((err) => {
  console.log(`something went wrong: ${err}`);
})

// if all went well process then, if not all went all, then process catch
// also have promise.race which takes the first one and processes the then
// efficiencies, send redundant requests to make things as fast as possible

Promise.all([
  promisifiedGet(url),
  promisifiedGet(url2)
])
.then((results, second) => {
  console.log(results)
})
.catch((err) => {
  console.log(`Something went wrong: ${err}`)
})


// ES7 version, something else introduced to make it more elegant. Check node and browser versions!
// heading here for error handling 
(async () => {
  try {
    // await waits for promise to finish running. value of resopnse if everything goes well. if error, await throws error, see catch. 
    // await can only be used inside functions, function needs to be declared as an async function
    // makes function become a promise
    let body = await promisiifedGet(url) 
    console.log("1st inside doGet", body)
    body = await promisifiedGet(process.argv[3])
    console.log("2nd inside doGet ", body)
    return body
  } catch (e) {
    console.log('bad bad bad', e);
  }
})

```
