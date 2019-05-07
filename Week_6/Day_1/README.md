#Week 6 Day 1 Notes
## Lecture Notes

* www.photopea.com
* React components

* Lighthouse labs react, boilerplate

* React is complicated to set up
* Use boilerplates
* Facebook has one
  * Recommend use it for the final, much easier
* Use LHL one today
* simplereactapp
  * reconfigure babel or webpack
* React will auto refresh, way faster

* What's the point of react? 
  * You can render an array {[1,2,3,4,5]}
  * Put in HTML into an array
    * let array = [
      <h1>1</h1>,
      <p>2</p>,
    ]
* Props are information you pass down to the next component
  * Always get passed in


* Rule 1: Always import react
  * import React, {Component} from 'react';

* Rule 2: Classes are your components
  * They will extend Component
  * Class App extends Component {}

* Rule 3: All components must have a render

* Rule 4: If component is in a different file, always export that component
  * export default App;

* Rule 5: Always wrap your JSX into one single element

* Rule 6: There are things called constructors and it has state. These are specific per class
  constructor(props) {
    super(props);
    this.state = { number: 0}
  }
  * To re-render, it must be in a state
  * this.state.number
  * this.setState( {number: x} )

* Potential Issues with React
  * Single page application
    * Challenging
    * EJS converting to React is hard

  * Security
    * Easy to hijack information coming in and out


* Good things about React
  * Example
    * Wrote a backend in 1998 in Java
    * Recreate all the routes and how it talks to the database
    * Easy to interchange back end, APIs
  * Very readable


## Breakout Notes

* More React
* Do another example, work step by step and build an applicatoin
* Focus on 2 things
  * Tooling
  * Properties, state and advanced features of react

* React is a javascript library
* Function component => Use them for output, display components only
* Anything that is a component in React, should be capitalized
* Keep state only in one place at the top of the app
* One place for the memory of the application

* 