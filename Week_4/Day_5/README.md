#Week 4 Day 5 Notes
## Lecture Notes

* User Auth
* 3rd parties like google, fb

* Remember that HTTP is a stateless protocol
* Need to use browser tricks to remember through requests
* First way is to use a cookie
  * Store it on the browser, send it in the header to the server
  * Keeps going on as if they know who you are

* Authetication 
  * Verify who you say you are
* Authorization
  * Up to web developer to say you have access or not
  

* Keys: [process.env.SESSION_SECRET || 'development']

* app.use(flash()); One time messages to the user
  * Passed as template vars to the template
  * Only works if reading out templateVar values
  * Only works if redirect to our own page

* morgan
  * shows the response codes and all the logs in the console

* Only call res.redirect once, return at end of if statement

* Always checking session id

* middleware will run each time request is made
* flow through 



```javascript
//Auth middleware

function authMiddleware(req, res, next) {

  // no session no user
  if (!req.sssion.user_id && req.path !== '/login') {
    req.user = null // make suer usesr is logged out
    res.redirect('login')
    return
  }

  User.find(req.session.user_id)
  .then((user) => {
    req.user = user
    next()
  })
  .catch( () => {
    req.user = null
    next()
  })
}

function find(id) {
  return new Promise ((resolve, reject) => {
    knex('users')
    .select('*')
    .where({id:id})
    .limit(1)
    ...
  })
}

```

* Passport JS
  * Library to handle authentication
  * Drop into any express based web-app
  * Serialize user in the session, deserialize user from the session
  * 3P login is hard to get data back to our page
  * Act as that user on that platform
  * ie. post tweets on their behalf, find friends list on facebook
  * get access token back from google that we can use to access the API
  * Use access token as API key, webapp acting on behalf of dave
  * Also get a refresh token, can get offline access as well
  * Use refresh token once access token has expired, gets a new access token
  * Login with google
  * user password prompt, then do you give permission to this app to access? 
  * then app gets acess to everyone
  * in get('/auth/google)
    * specify the scope: ['openID profile email]
  * use passport if you want more than one authentication strategy
  * oaut.net

``` javascript
passport.use(
  new LocalStrategy(
    {usernameField: 'email', passwordField: 'password'},
    (email, password, done) => {
      User.authenticate(email, password)
      .then((user) => done(null, user))
      .catch((error) => done(null, false))
    }
  )
)

```