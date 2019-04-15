#Week 2 Day 2 Notes
## Lecture Notes

* TinyApp - Project to be done over next few days
  * All to do with web

* Your machine could be a server
  * Server could be any computer that is willing to serve
  * Serve whatever information you want (it has)
  * Request and response
  * Unit of the web is I have a request and somewhere someone has a response

* Be a client, how to ask for something
  * Use javascript,  browser, terminal (curl)
  * Javascript needs particular library that knows how to send a request
  * Server doesn't care where request comes from

* What does it mean to be a server?
  * localhost:8000
    * Special URL called localhost, no matter what points to own machine
    * 8000 is a port, 80 is by default
    * Being organized to serve a response to every request

* Within the call back, explore the request and dictate the response

* Express
  * app.get call backs
  * need npm install express
  * Separate into control and views
  * EJS html pages can be rendered on to server
  * EJS files can be modified while server is still running
  * Inspect and see that generated date is pure HTML without the javascript code
  * All JS code that is in ejs runs in server before dispatch to HTML
  * <% var city = "Toronto; 
    var today = new Date();
    var forecast = "cloudy"%>;
  * <%=city %>
  * <%=today %>
  * <%=forecast %>
  * /static/filename
    * static is defined in server 

* Model View Controller
  * Data, brains
  * Display, view
  * Everything is in own place
  * Change how a page looks, go to View
  * Change logic and how it works, go to Controller

* Practice alot of express over the next few days
* How you can build up server by adding new features

* Look through notes, get help on TinyApp project


## Breakout Notes

* Ship ES5 code to browser but write it in ES6
  * Cannot yet ship ES6 to browser
  * Takes long for browsers to implement
  * Counting on browsers and javascript engines to adhere to the spec
  * ECMA script code shipped to browser is executed by javascript engine
  * Code for V8 (Chrome) is open source if we want to read it
  * node uses V8 as javascript engine
  * MS announced recently it is switching to V8 and abandon their own
  * Chromium is open source
  * ES7, ES8, ES.Next

* What versions are we shipping?
  * It doesn't matter
  * Use tools called transpiler and polyfills
  * Allow us to develop in whatever we want, take the code down transpile it to ES5
  * Use Babel to convert from next-gen JS to browser-compatible JS

* What if we just want to use one feature from ES6? 
  * ie. Set feature
  * Don't want transpiler, don't want to write in ES6
  * Polyfill checks if Set is compatible, if it does do nothing
  * If not supported, inject code necessary so that we can call it in our code

* Features of ES6
  * One from ES5 
    * 'use strict' is a directive to JS engine
      * Interpret code in strict mode, not allowed to do somethings
      * ie. variable assignments that are not scoped
      * Error out, code will not run
    * eval
      * Take a string and run as javascript
      * Dangerous and slow
    * with
    * can call 'use strict' on a per function basis, ie. first line of a function
      * function executes in strict mode

  * String interpolation
    * Template literal with `` to define string
    * Write javascript expressions within ${}
    * ie. console.log(`My name is ${person.name} and my age is ${person.age}`);
    * console.log(`324 * 543 = ${324 * 543}`);

  * for...of
    * loop over iterals including array and strings
    * map and set types added
    * for (var x of arr)
  * for...in
    * loop through object

  * let and const
    * let is block scoped
      * function with a for loop var i counter, before counter i is undefined, hoisted from the function, afterwards can access the value
      * function with a for loop let i counter, i defined within the loop, scope of where i defined. i undefined and undeclared outside of loop
    * const 
      * const prevents reassignment, cannot reassign a new value to this variable
      * const object still pointing to same thing, but can add to the object / array
      * const is also block scoped
      * ie. const konstant {quality: "unchanging"};
      * delete konstant.quality
    * Keep scope small with let
    * Up to you which to use. Use the best one for the job. 

  * arrow functions
    * Improve way to declare small simple functions
      * var add2 = (x, y) => {return x + y};
      * var add4 = (x, y) => {x + y};
      * var double = x => x * 2;
      * var doulbe2 = (x) => x * 2;
    * Binding for this different for standard function vs arrow function
      * var test = {
        prop: 42,
        func: function() {
          return this.prop
        }
      };
      console.log(test.func());
      * this refers to the object that invoked the function
      * object test is invoking func, this refers to test
      * var test = {
        prop: 42,
        func: () => {
          return this.prop
        }
      };
      * this is undefined, not bound hte same way
      * this takes lexical scope at the time the function was declared
      * TAKEAWAY: Binding of this is different for arrow functions and regular declared functions
      * Will see more of this in REACT
      * Start to use ES6 now

  * ECMA TC39
    * Controls updates
    * Can submit propsals in 
    * Different stages of proposal, strin




