#Week 1 Day 5 Notes
## Lecture Notes

* Modules and Testing

  * Every javascript file is a module

  * Math notation ** equivalent to Math.pow(), number by exponent of value

  * exports
    * Example 
      exports.area = function (r) {
        return Math.PI * r ** 2;
      }


  * require
    * var circle = require ("./circle");
    * file gets executed as is when require called

  * Area calculation
    * Problem of display vs problem of calculation
    * Separate data vs how it's displayed

  * What is responsiblilty of each of these modules?
  * Single respnosibility principle
    * Each module has 1 responsibility only
    * Keeps code easier to change without breaking
    * Protect ourselves against unintended changes, to be discussed later


  * add.js
    module.exports = function(a,b) {
      return a + b;
    }

    in index.js
      var add = require("./add");
      add(2,2);

    * Exports entire function as opposed to object containing function previously

  * Modifying exports object vs adding definitions to exports object
    * exports.area, exports.circumference
    * module.export -> reassigning it to a function
    * Why cant just reassign exports?
      * exports = function () {}
      * Reference variables example, just creates a new variable in the scope rather
      than changing original objects values
      * Need to do it as module.exports

* NPM
  * Allow pull in 3rd party code / applications into our library
    * Why re-invent the wheel?
  * Package managers useful b/c things pulling in has dependencies themselves

* How to use modules? 
  * Make our own node package
    * npm init
      * create a package.json file (javascript object notation, serialize into strings; parsers to convert back)
        * package name? (default in brackets)
        * version?
        * description?
        * entry point
        * test command
        * git repository
        * keywords
        * author
        * license (ISC or MIT, GPL) do own research on it
        * Confirm OK
      * package.json file created
        * keys always quoted
        * at top level always object or array
    * npm install request
      * when library installed, saved in package.json as well (since node 8)
        * dependencies added
          * key name is library, value is string with version that we are using ^2.88.0 (anything 2.88.x)
      * creates package-lock.json
        * never modify this file
        * goes through dependencies and lists versions when npm install ran
        * when sent around, get same versions of npm dependencies installed
        * calculate a hash for each module, things installed is what they say they are etc.
      * created node-modules directory
        * needs somewhere to store all js files
        * even though we required single module, built on top of other modules that are required
        * never commit node-modules to git
          * no reason to
          * bloat git repositories
          * as long as package.json and package-lock,json are included, modules can be reinstalled
      * gitignore
        * # NPM stuff
        * node_modules

* Testing 
  * Mocha
    * Write code that is going to test our code
    * Framework running our tests
    * Write tests and execute tests, report statistics etc.
  * Chai
    * TDD / BDD 
    * Assertion library
    * Tools to be able to create assertions and to be able to say
      * Should
      * Expect
      * Assert
  * Range, act and assert are 3 criterias for any test 
  * npm i --save-dev mocha chai
    * plain dependencies are required to run
      * ie. request
    * development dependencies are tools, other pieces of workflow, not necessary to run,
    but used in workflow
  * mkdir test
    * touch test/add_test.js
  
      * Semantics, all test files end in _test to differentiate from application code
      
      * var expect = require("chai).expect; 
      var add = require("../add");
      
      describe('add, function() {
        it('should return 4 if we add 2 and 2 together', function(){
          var expected = 4;
          var result = add(2,2); // could have put 2 and 2 into variables in arrange section, but not needed here

          expect(result).to.equal(expected); // or can also say 4 instead of expected

        });

        it('should return a number', function(){
          expect(add(2,2)).to.be.a("number);
        });
        it('returns null if any parameter is a string', function(){
          expect(add("2","2")).to.equal(null);
          expect (...) // can add similar tests in here, ie if one is number and one is string
        })
        
      });
      * scripts added to package.json, look for test scripts to be run
        "scripts": {
          "test": "mocha"
        } 
        * mocha will find and run through test and print a report
        * execution of tests doesn't go past failing test
        * use different values to 

  * avoid using typeof
    * unary operator, appears before a value
    * typeof is okay to use sparingly, but don't use it to determine values and logic

  * javascript the good parts book

* Mock Test
  * Practice working inside test environment that we have
  * Get test runner to run, fix environment issues
  * Bunch of tests, module with a function, work is to get it to pass associated tests
  * 2 hours to write it, start at 4 PM
  * Got until Monday to wrap it up
  * Open book, stay away from StackOverflow, don't look up answers

  
