#Week 3 Day 1 Notes
## Lecture Notes

* Week 3 will feel like it's slowing down, now that we are used to it
* Talk about HTML and CSS today
* Tweeter project this week
  * Very different from TinyApp
  * Every thing orchestrated by server in the past
  * Explore a new paradigm called single page application (SPAs)
  * No server, everything done by the application
  * This started around 2006 when mobile phones came out
  * Talk about having computers in our hand this week

* How do we make the browser more powerful, better looking, faster and able to connect to more things?
  * Look at HTML and CSS

* CSS is tough to master
  * We don't need to learn everything
  * Learn basics and tips and tricks today 

* In the 90s, HTML what you see is what you get
  * Social trick back then, to have linked lists
  * Already came across lists that were very good
  * At the end of own page, add a simple list of other pages that "I" think are also good
  * Simple social contract
  * Start of semantic web
  * Links started to become annotated with a blurb
  * This started to become blogs
  * You can tell them apart

* Transition from thinking of HTML as a tool for structure to a tool for semantics (what are the things hear and what do they mean)
  * One milestone in the early 00's
  * ie. List of ingredients on a recipe were important part
  * Special delimiters created for just the list of ingredients
  * Microformats for semantic HTML
    * ie. <ul id ="recipe">

* Blogs were the start of social media
  * Leave comments
  * Social media is the snark without the content

* Fast forward to the semantic web
  * Web page with movies, need to make sure look at 3 elements
  * Movie poster, title, show times
  * Well annotated, google will serve content from pages and leave page behind
  * How do we extract information about everything that has been written?

* <body>
    <header>
    <main>
    <aside id="weblogs">

  * MDN Semantic HTML for more
    * <section> will be used alot
    * Main lesson here is that all the semantics happened more recently
  
  * Style links in <aside> differently than links that are everywhere else
    * <style>
      h1 {
        font-family: arial;
        font-style: 16px;
      }
      li {
        margin: 5px 20px 5px 20px
        padding: 3px;
      }
      aside li {
        background-color: salmon;
      }
      .Publisher{
        background-color: lightblue;
      }
      main {
        width: 65%; // padding
        float: left;
      }
      #weblogs {
        width: 35%;
        float: right;
      }
    </style>
    * <h1 style="font-family: arial:"> for specific style changes
  
  * Developer Tools Inspector
    * See that elements have inline styles in element css
    * Also see CSS rule styles (ie. applies to all h1 elements)
    * Write styles in element (same as inline CSS)
  
  * Competing styles
    * Where are styles coming from? 
    * Frameworks
    * Browsers
    * Most of battle with CSS is how to get my rule to over rule your rule

  * CSS is cascading
    * Elements within are all styled from parents
    * ie. style to a list item applied to links in the list
  
  * Realize that everything on a page is a block or not (inline element)
    * Block element tries to grab as much as it can from the page
    * Nothing else can be put on the same line
    * ie. <div>  within a <li>
    * Browser will put next block right underneath
    * Changing the block
    * Block can be sized (ie. only 200px)
    * Figuring out the decisions the browser makes is not trivial and requires experimentation
    * Inspector will help

  * Trick
    * { (apply to all)
      border: solid 1px red;
    }
    * CSS Box Model
    * Other areas not shown
    * Margin is something that surrounds the element
    * Padding is the inner margin


  * <span class="Publisher">
    * Inline elements
    * Add margin
    * Can't size them, sized based on contents they have
    
  * box-sizing property 
    * box-sizing: border-box;
    * 60% and 40% split, don't forget to count the border and padding
    * Margin isn't accounted for in this border-box

  * CSS should be at the top of the document
  * Try to write the rules following the structure of the document
  * If CSS grows too much, migrate it out of the page
    * <link href="/cssfile.css" rel="stylesheet" >

## Breakout Notes

* Follow up to this morning
  * Can imply things about the tags
  * ie. Forecast
  * dl, dt, dd. Detalied list, dt is item, dd is descriptions
* Rules about CSS
  * Tips to evaluate CSS
  * If there is a duplicate, CSS will opt to use the last one in the stylesheet
    * Put your CSS rules at the bottom of the style sheet
  * ID are more important than classes
    * Only once per document
  * CSS assigns a value to each rule
    * ID worth 100 points, Class worth 10 points
    * Inline worth more than either of these (1000 points)
    * When two rules are candidates, the one with higher score wins.
    * Rule with more than one class worth 10pt for each class
      * .weekday .number {}
      * #today time {}
        * ID, element name
        * Tag element by itself is 1 point
        * Parent and child means somewhere within, not directly with in
    * Stick to classes in general
      * Creates a uniform look across document
    * More specific rules will take effect
  * Direct child selector ( > )
  * Adjacent Sibling selector ( + )
    * Only takes the first adjacent sibling selector
  * General sibling selector ( ~ ) 
  * Display: block
    * display: none
  * Centering
  * In general, don't try to position things manually
    * ie. larger, smaller, 40%, try to be relative
  * Positing things relative to the parent
    * ie. move dd closer to dt
    * element: {
      position: relative
      left: -10px
    }
    * try not to go there, as opposed to letting things flow in the best possible way
  * Talked about concrete rules for css, combinators, specificity, gotchas
  * Tweeter the project is alot more about attention to detail
  * It's okay to spend more time to get it looking right
  * ie. 
  <style>
  #forecast {
    width: 60%
    margin: auto;
  }
  .weekday {
    background-color: aquamarine;
  }
  #today {
    background-color: pink;
  }
  #forecast time:hover { /* if hovered then style this way */

  }
  .daylist ,weekday time {
    background-color: lightgreen;
  }
  dt .weekday { /* class weekday that is inside a dt, this is different than dt.weekday, dt that are also weekday*/
    background-color: lightgreen
  }
  .dayList > dl > dt > time {

  }
  dt + dd {
    background-color: lightblue;
  }

  dt ~ dd {

  }
  
  </style>