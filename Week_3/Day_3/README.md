#Week 3 Day 3 Notes
## Lecture Notes

* 99% of web development uses javascript to do 2 main things
  * Dynamism, hit something on one page without navigating away

* AJAX loads page in smallest possible state
* Do more things based on user activity, or tracked behaviour
* Asynchronous Javascript and XML
* A synchronous language runs from top to bottom and is blocking
* ie. 3 different get requests
  * get comments before rendering
* Infinite scroll is AJAX
* AJAX as a function is used to communicate with server asynchronously
* Progressive web applications
  * If you don't have latest javascript, then fall back
  * If you don't have javascript, can't use AJAX
  * jQuery.AJAX
* AJAX is not a tangible thing, more a methodology like CRUD / REST
* Server returns faster when they return JSON than rendering HTML
* Get data and spit out JSON rather than piece togehter HTML and CSS
* Add .json to end of any subreddit gets all data back
* Don't run server at all, only use 2 files
* HTML and Javascript file
* Emmet, type ! and hit Tab
* Get post, handle success, error handling

* Reading and debugging is more important than packages downloaded
* Google things in package.json 
* Use Axios common http handling library
* Use CanIUse to check if things work
* Run Babel that transpiles things back to IE3 / IE5

* CORS ( cross origin resource sharing)
  * On a website, and make a call to another website
  * Local host 3000 error
  * Look for white listed address, have API token, username / PW
  * Reddit has turned off CORS on anything subreddit.json
  * Fetch from our site and not get an error
  * Google API would give us 403 unauthorized, or in header of HTTP request tell us to turn CORS off
   
* Bearor token
  * API Token
  * Before send hook, set header for authorization to bearor token
  * Authorized API or not

* Document.ready is used for jQuery
  * Alternative
  * document.addventListener("DomContentLoaded", function() {

  });

* Start by doing something async
  ```javascript
  const title = '<h2>Hello, LHL!</h2>'
  const clickHandler() => console.log("I have been clicked")
  $(document).ready(() => {

    //setTimeout() => {
      //const h2 = `<h2 onclick="clickHandler()">${title}</h2>`;
      //$('.title').html(h2);
      ////const otherH2 = document.createElement('h2').text(title);
      ////$('title').append(otherH2;)
    //} , 2000);

    $('.title').html(title)
    $.ajax({
      type: 'GET',
      url: 'https//www.reddit.com/r/dogpictures.json'
    })
    .done( response => {
      response.data.children.forEach(post => {
        const {title, permalink, thumbnail} = post.data;
        
        const markup = `<a href="http://reddit.com${permalink}" target="_blank"><img src="${thumbnail}" title="${title}"/></a>`

        $('.content').append(markup);

      })
      // post.data.title
      // post.data.thumbnail
      // post.data.permalink

    })
  })

  ```

