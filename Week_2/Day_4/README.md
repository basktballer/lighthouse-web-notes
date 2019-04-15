#Week 2 Day 4 Notes
## Lecture Notes

* Talking about cookies
* Common problem that the Web was designed to be stateless
  * Everytime we make a request to a server, it responds and its done
  * The next request is brand new
  * ie. when was the last time FB forgot about you

* Web was designed where everyones computer was a server
* Set a cookie
  * res.cookie('preference', en)
* Middleware
  * Create new custom features with Express
  * // use express to call the following function to run every tim ethere is a request
  * Called middleware because it happens in the middle4
  * app.use(callback)
  * See request, response and next
    * Make sure to call next at the end of the function
  * ie. app.use(function(req, res, next) {
    console.log("Request: ",req.url)
    console.log("Headers: ", req.headers)
    next()
  })
  * cookie stored in request.headers.cookie
  * Use cookie-parser to pull cookie into req.cookies
    * const parser = require("cookie-parser")
    * app.use(parser('you should be just fine'))
    * phrase is used to determine the hash for cookie signing
  * Few things about cookies
    * My browser my rules
    * Preferences, edit cookies to change it to whatever 
    * Cookie is the users cookie
    * Be careful what is stored in the cookie
    * Can't trust user to store important information
    * In Console
      * document.cookie = "preference=FR"
    * res.cookie('preference','EN', {signed: true})
      * create a signature and add it after the cookie
      * Signature confirms that cookie data has not been changed / manipulated
    * When you used a signed cookie, not protected or invisible
      * Only proof that it hasn't been tampered with
      * Don't store pw in there thinking it's secure
    * When a cookie is signed, cookie-parser will organize them to Signed cookies
    * Confirmed by cookie parser that it is not tampered with, value displayed
    * Cookie value returns false when it has been tampered with
    * look at signedCookies
  * More advanced cookie
    * Cookies cannot be trusted, users are in charge of them
    * second redirect to login page, generates a cookie
    * signed cookies can be used in another browser
    * Can be stealed from being on the same network (ie. starbucks)
    * Don't trust signed cookie to hold anything infomration
    * https can take care of it
    * for important information, don't give away the information in the cookie name and cookie value
    * best practice, store or use a random number instead of username
    * Generate a token uniquely associated with the user
      * Keep a database on the back end including user token
      * Can expire the cookie and force to generate again (ie. every 10 minutes)
      * Reduce window of opportunity for someone to take over the situation
    * function createToken() {
      Math.random().toString().substr(5,5);
    }
    * Create the user, store by cookie token
    * Don't store clear text passwords
    * Encrypt instead
      * console.log("password: ", req.body.password);
      * console.log("bcrpyt: ", bcrypt.hashSync(req.body.password, 15));
      * Encryption is always gonna render the same result
      * Every password has an encrypted value
      * Every check, encrypt the password and compare
      * When the user signs up, the password is the encrpyted version
      * Push it to the DB
      * Cookie call username, and put uniqueID {expires: new Date(Date.now()) + 5}
      * When login check username and pw are same as provided
      * Checklogin(username, password) {
        bcrpyt.compareSync(password, user.password)
      }
      * valudUser(username) 
      if(user.unique === username) {
          return user
        }
      }
      * Check encrpytion only once because it takes a long time, else validate the username
      * Have passwords stored on server encrypted, and only use cookies that are tokens that are meaningless and for specific sessions
      * Lots of people use the same passwords
      * Can do statistical analysis to see who are using the same passwords
  * How does FB know who I am? 
    * www.wired.com
    * Cookies per website visited are unique to the site
    * Cookies and ad cookies
      * When visiting the website, have ads placed
      * Website is visited to have ad show
      * When ad showed, the cookie gets placed there
      * Each one of these ads served by a different machine somewhere, and each sets up a cookie associated with this session
      * ie. Google knows if you visit wired.com and facebook.com, seeing same ads everywhere
      * Visit facebook once a month, associate who you are with entire where you visit
      * See the facebook like button, served
      * Best way is to be mindful, once in a while reset cookies
      * Firefox -> restrict facebook usage to unique session
      * Incognito is browser without cookies
      * Then data is sold

* Tips
  * Remember npm install --save saves to package.json

