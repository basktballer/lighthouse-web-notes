#Week 3 Day 2 Notes
## Lecture Notes

* Comparing type of activities that you like the most, start to get a feel for what means to be a back-end developer vs a front-end developer
* Separation of the engine from the browser became Node js
* Today looking at the javascript that runs in the browser
  * Everything done in Javascript can be done in the console



  * A few objects declared for you ahead of time
    * Console commands: 
    * Window.location.href
      * Matches location in location bar
      * Change the url in the browser by changing the object in the code
    * Window.history.back()
    * MDN Web APIs - Window
    * Window represents the browser window
    * navigator.userAgent
    * navigator.geolocation.getCurrentPosition(pos => {
      console.log(pos)
    }) // Get current position in javascript (lat and long)
    * document // AKA window.document
      * Interactive document, when mouseover, page goes blue
      * Document is my page, 

    * let title = document.getElementById("firstHeading")
    * title.innerText = "Juan Gonzalez"

    * let images = document.getElementsbyTagName("img")
    * images[0].srcset = //*insert link*
    
    * let list = document.querySelector('#toc ul') // search by CSS tag, -> Table of Contents and ul within
    * let todo = document.createElement("li") // created as a variable, but not attached to HTML
    * list.appendChild(todo) 
    * todo.innerText = "Dont forget to add the innerText"

    * title.innerHTML = "Juan Gonzalez <button>Verify!</button>"
    * myButton = document.querySelector("button")
    * myButton.addEventListener('click', function() {
        alert("Verified!");
      })
    
    * title.addEventListener('mouseover', function(ev) {
      console.log("Event: ", ev)
    })
    
    * function $(query) {
      return document.querySelector(query);
    }
    * function $$(query) {
      return document.querySelectorAll(query);
    }


  * Every page has it's own javascript object, once you move to another page, it is lost
  * Javascript the language was supposed to be an automation engine
  * Javascript can enable developers to be border line creepy 
  * Browser provides a sandbox for developers, once window is closed, developer can't get access to personal files
  * Learn the process of modifying document through javascript
  * Illusion of speed, show empty page, then javascript processes what it will show first
  * Used to improve the perception of how the page works
  * Use Javascript to watch scroll bar, as get to the bottom load a new item, infinite scroll
  * When changing HTML through DOM, be careful
  * Have ability to change contents of a page through code
  * Any HTML changes
  * Be careful letting HTML into code from outside sources
    * can enter Tacos <script></script>
  * HTML injection is a real threat
  * Use innerText to change contents of a page as opposed to innerHTML
  * Event Driven Programming
    * Different from writing code in step driven mindset
    * User decides when to trigger different events
    * Most browser based applications are built like this
    * What should I do when I click this button
    * Event listener is always listening, event loop keeps running
    * Not in control of the event loop, the browser is
    * In a given event loop, if any event is found, doesn't wait for callback to come back, keeps iterating
    * Callbacks themselves, if that code has any sort of I/O, the I/O may stop computer from doing other things, but javascript keeps running
    * Main loop is happening on a single thread and runs all the time
    * Javascript single threaded but can run I/O blocking operations on a separate thread
  * Have as many event listeners as you want on a page
  * Typically have it on every button, every form, most links
  * Rule : Inner most event triggeres first. It can stopPropagation 
  * Hijack what a form does
  * Event machine is very fast, just north of 60fps
  * Any browser game is built off of this


## Breakout Notes

* jQuery
  * Cross compatibility issues across browsers
  * Syntactical sugar
  * CSS selectors
  * Ajax -> network requests that uses jquery
  * Wordpress
    * Plugins exist
  * jQuery plugins were created in its own ecosystem
    * Carousels, drop downs, simple animations
    * Lots of prebuilt UI with dependency jQuery
  * No additional behaviour that we couldn't achieve with regular javascript
  * jQuery is a library
    * expose helper functions to query on DOM, make Ajax requests, 
    * String things together
    * No steps to string things together
  * $('div')
  * $('button').siblings('input')
  $ ('input').val('content')
  $('<li>')
  var item = $('<li>'.text(content)
  $('li')
  
  * jQueryUI
    * accordion
    * widget buttons
    * date pickers
    * only dependency is jQuery

  * Why is it important to learn jQuery?
    * libscore jquery 692K
    * 70% of top 1M sites use jQuery
    * 2 problems that it set out to solve
      * Browser compatibility 
        * Browser API standards have converged
      * Syntactic sugar 
        * Not as big of a deal with ES6

  * You might not need jQuery
    * website

  * jqLite
    * Minimize amount of data loaded on mobile, use jqLite

  * Trigger the main javascript at end of page
    * If DOM elements not loaded when script loaded, it won't work
    * User experience could be bad while waiting for js to load

  * event object
    * offsetX, offsetY
    * capture event information
    * console.log(evt)

  * console.log(this)
    * grabs the dom node, object that invokes the function
    * when you click the dom element, invokes click handler, this refers to the dom element that was clicked to invoke click handler
  * console.log($(this))
    * console.log($('button-prize-btn'))
    * take Dom element, pass into jQuery function and create a jQuery element
  * use 'on' keyword rather than custom words


  * Example 2
    * use this to specify which object invoked
      * var btn = this;
      * var $btn = $(this);
      btn.siblings('.prizes').append('you win a prize!');
        * btn.siblings doesn't work
      $btn.siblings('.prizes').append('you win a prize!');
      * $ in front of variable name is a convention
      $btn.closest('.prizer').find('.prizes').append('you win a prize!');
      // look up for parent prizer, look for child prizes, append you win a prize
      // closest only works because they are wrapped in prizer
      // if not, then have issues
      * is there a best way and how do we figure it out? 
      * least number of checks on our Dom is the best
      * 
      $(".prizes").hover(function() {
      $(this).css("background-color", "yellow");
      }, function() {
        $(this).css("backgound-color", "white")
      });
      * CSS didn't use to have the hover ability, part of why jQuery gained popularity
      * What is the rest of code doing? Keep it simple, if everything jQuery then use jQuery. 
      * Detailed animation transforms, do them in CSS, can offload some of it onto GPU
      * Starting from scratch, put it into CSS 
      * Simpler to understand
      * Unless its already everywhere, then use the jQuery

  * Example 3
    * Show pets button
    * Dynamically inject pets into page
    * Inserting elements into the DOM
    * var newPetElement = $(`<p>$(item.name)</p>`)
    var newPetElement = `<p>$(item.name)</->`
    