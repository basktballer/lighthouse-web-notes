#Week 2 Day 1 Notes
## Lecture Notes

* HTTP & APIs
  * Web Server vs Web Client
    * URL - Uniform Resource Locator
      * http://www.example.com:8080/hello?name=faisal
      * http        protocol
      * wwww        host
      * example.com domain
      * :8080       port
        * (default port that web listens to, 80, if changed from default, we have to include it. Every server has to listen to its own port)
      * /hello      path
      * name=faisal parameter
    * TCP/IP
      * Collection of protocols for different scenarios
        * Transport Control Protocol
          * Take all data from one site to another, label and make sure it makes it to the other end
          * If one piece doesn't make it, TCP asks for it again to make sure it makes it
          * Ensures order (ie. emails and videos aren't out of sequence)
        * Internet Protocol
          * Responsible for addresses
          * Packets and pieces make it to the right destinations
          * IPV6
            * 64 bits of addresses vs 8 bits for IPV4
        * Application Layer
          * Both client and server has to have same layers in order to communicate
            * ie. Transport Layer on both sides
            * Application -> Transport Layer -> Internet Layer -> Physical
          * FTP
          * SMTP
          * HTTP (web transfers)
  * HTTP Fundamentals
    * How does URL become IP Address?
    * DNS - Domain Name Service
    * Wifi connection tells you which DNS its connected to, configured by LAN provider
    * Know IP Address of DNS and URL
      * DNS send the IP address that corresponds to the server of the URL
    * HTTP Responses
      * Later in the week, we'll do a 301 redirect
        * Send a new address, browser takes it and sends a new request
      * 403 Credentials issue
      * 404 Not Found
      * 500 Related to Web Application Server
        * Bug in code, express server
  * Request / Response
    * Request GET, resource, http, host
    * Response Http, success code, date, content type, content
  * HTTP Methods
    * GET and POST are most typical
    * Before POST, we have to do a GET
      * Typically, need to get the form to be filled in, render it
  * API Endpoints
    * Windows into what's there behind the wall
    * API only exposes some of the data
    * Whoever controls the data, controls the API
    * Find all kinds of API
      * Pay a fee for consuming data
      * Public APIs (ie. google, spotify)
      * Depending on what you are trying to do
    * Spotify API Example
      * REQUEST /albums
      * RESPONSE JSON format
          

## Breakout Notes

* API is an interface
  * Endpoints that we can use standard HTTP methods on and pull things out
  * Most APIs use REST and return JSON
  * MetaWeather is presented in HTML, can pull the information out but HTML changes frequently
  * API is a way to provide people with a standard way to access the data
  * API are versioned

* request.get()
  * Each request.get is asynchronous and depends on when response is received
  * write out functions and reference them in get request to ensure that things are being done at a time