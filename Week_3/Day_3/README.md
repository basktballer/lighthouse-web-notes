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
* Use Firacode github, install on machine
* Bracket colorizers
* Babel, ESLint

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

* Throttle performance on browser and see how long it takes to load all images, Network tab


*  how server is handling, (reddit not handling message) sent in responseJSON
// also error message itself coming back as empty string
// ie. change password, error message would come back from the server
// often server return messages with status, depends on 



* Code Example
  ```javascript
  const title = '<h2>Hello, LHL!</h2>'
  const clickHandler() => console.log("I have been clicked")
  const handleClick = () => {
    const subreddit = $('#subreddit-input').val();
    
    //setTimeout() => {
      //const h2 = `<h2 onclick="clickHandler()">${title}</h2>`;
      //$('.title').html(h2);
      ////const otherH2 = document.createElement('h2').text(title);
      ////$('title').append(otherH2;)
    //} , 2000);

    $('.title').html(title)
    $.ajax({      // ajax is asynchronous, runs as soon as document ready
      type: 'GET',
      url: `https//www.reddit.com/r/${subreddit}.json`,
      dataType: 'JSON'
    })
    .done( response => {  // do not do anything until .done. Intentionally blocking. .done is as same as .then in Javascript promise
      const markupArray = [];

      response.data.children.forEach(post => {
        const {title, permalink, thumbnail} = post.data;

        if (thumbnail !== 'self' && thumbnail !== '') {        
          const markup = `
            <a href="http://reddit.com${permalink}" target="_blank">
              <img src="${thumbnail}" title="${title}"/>
            </a>
            `

          markupArray.push(markup);
        }

      })

      const formattedMarkup = markupArray.join('')
      $('.content').append(formattedMarkup);
      
    })
    .fail( (XHR) => {

      const {error, message} = XHR.responseJSON

      const errorMarkup = `
        <div style="background-color: red">
          <h2 style="color: white">${error}: ${message}</h2>
        </div>
      `
      $('.content').append(errorMarkup);
    }) 
  }

  $(document).ready(() => {



  })

  ```

* AJAX Examples
  * AJAX under the hood is
    * xhttp.open( "GET", "ajax_info.txt", true)
    * xhttp:send()
    * xhttp.open("POST", "demo_post.asp", true)
    * GET not better than POST
    * Data attached to request through POST
    * GET attaches them in URL parameters
