#Week 3 Day 5 Notes
## Lecture Notes

* Responsive Design + SASS
  * CSS native has already improved
  * Eliminate the need for things like SASS
  * Add in 2 things that aren't in the lecture
    * Flex box and CSS Grid

* Responsive Design
  * Work on any device / resolution
  * Responsive up to a point and then get side scrolling
  * Side scrolling is the enemy of hte internet
  * Compass -> Certain things go away / reposition
  * Resize based on the size of the browser
  * ie. on a mobile view, hide the calendar
  * More than screen size
    * It can mean type of screen, print screen, portrait vs landscape
  * Google responsive web design basics course
  * Realign elements to viewport size when they have an awkward amount of spacing
  * Scaffold html page
  * Margin is space between elements
  * Padding is space between contents and its borders

  * <meta name="viewport" content="width=device-width, initial-scale=1.0">
    * set viewport on mobile devices for desktop width pages
    * matches what one pixel on the screen to one pixel on the display
    * ie. Galaxy S5 only has 360 width, but 500px design

  * change height of a div to 100% why doesn't it get bigger? 
    * % is % of parent element
    * body is only as tall as it gonna be
    * display block, causes it only to be as tall is it 
    * use 40vh
      * viewport height
      * only use vh at the highest level of the webpage
      * cool to use it on the container
  * width 
    * 100vw
  * box-sixing: border box
    * everything stays within the defined width as opposed to on the outside of the box

  * pixel values
    * use pixel for borders is okay
    * 2 -3 - 4 500 pixel values does not mean the same on the phone as on laptop
  
  * % are good in side things
    * good for children of container elements
    * relative to the parent element 
    * good to have container elements to hold things

  * min-height 

  * em -> width of letter M of based font-size of it's parents
    * em is bad because resetting default font sizes is bad (ie. font-size: 20px;)
    * relative to it's parent container size
  
  * rem -> root em
    * root em mapped back
    * can still use em for children elements
    * can also use it for padding

  * media query
    * some developers will do the site on their screen then use media query resize on mobile phones
    * not great b/c mobile has the slowest phone

  * write mobile first CSS
    * base css for mobile
    * anything over a screen size do something extra
    * see a lot less CSS when writing mobile first

  * hyper performant css
    * only link to (load) css files, no css read until media query is read
    * until it comes back (> 1000 px) then css won't be loaded yet
    * not really ok
    * only do it for media = print

  * Sass
    * Imports and operator
      * Google Fonts
      * Use @import, native to SASS
    * Limitation of Sass
      * Can't use javascript to change variables
      * They don't exist when you get to the page
    * Native CSS variable
      * Use Javascript to change it in real time

  * Flexbox
    * Flexbox Froggy
    * Grid garden
    * Defaults set
      * flex-direction: row // can use column
      * flex-wrap: no wrap; // when no more room for element, stick it below the sibling element
    * Flex is responsive out of the box, not exact
    * flex-basis should be 33%
      * can be smaller and larger because not setting flex-grow, flex-shrink
      * If another dimension is more specific, resize flexibly
    * Order
      * Accessibility
      * Re-order using CSS
      * Screen reader will hit main content, rather than aside stuff, even though aside shows up first
      * Use Javascript to change the order of a specific element
    * good for 1d layouts, left and right, or top and bottom
    * example 3 x 3 grid would look good on mobile only
      * flex flow, column no wrap


  * Grid
    * good for 2 d layouts, left and right and top and bottom
    * can make grid areas and assing things to area
    * Use javascript to change items live
    * repeat, how many times and what the value of the thing is
    * Dashed lines around grid items
    * Firefox is better for looking at grid

  * css root
    * use to declare variables --background-color: green;

  * &:hover operator
    * only available in sass

  * @import
    * exists for CSS for google fonts
    * not for partials, ie. sass file with all variables inside

  * Asides
    * Alot of websites designed using rule of 8 
      * base padding is 8 pixels, 
      * base font size of browsers is 16 pixels 

    * Float makes things not display type block anymore
    
    * follow rachel andrew on twitter
      * perch css

    * 
