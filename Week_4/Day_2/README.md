#Week 4 Day 2 Notes
## Lecture Notes

* Databases are parannoid about data
  * Access, duplication
  
* Connect to database through Javascript
* 2 different set of rules
* In the Shell, its a local session
  * Restrictions are very loose
* Connect to same db from a remote computer
  * More strict set of rules
  * psql -d vagrant -U vagrant -h 127.0.0.1 -p 5432 -W
  * database, user, host, port, ask us for a password
* Network connection, remote PC to database is secure
* Javascript will act as a remote connection to the database
* What could be wrong in authetication process?
  * User does not exist on database

* Use npm install pg
  * Driver to connect to postgres, not database itself
  * 

  ``` javascript

  module.exports = (function(){


    const { Client } = require('pg')
    const client = new Client()

    client.connect()

    function titleofalbum (callback) {
      client.query('select title from albums', [], (err, res) => {
        if (err) {
          console.log("we found an error")
        } else {
          callback(res.rows[0].title); //forEach(row =>  = row.title)
          }
          //console.log(err? err.stack : res.rows[0].title)   //response comes back in an array of rows
          client.end()
      });
    }

    titleofalbum(function(output) {
      console.log("Title found", output);
    });

    function firstTrackOfAlbum(album, callback) {
      client.query('select title from tracks where album_id = $1', [album] ) // if no callback specified, then blocks as below
      .then(response => {
        callback(null, response.rows[0].title)
      })
      .catch(error => {
        callback(error)
      });
      
    }

    firstTrackOfAlbum("9", function(err, output) {
      if(!err) {
        console.log("Track found", output);
      } else {
        console.log(err);
      }
    });

    function tracksOfAlbum(album, callback) {
      client.query(`Select tracks.title from tracks, albums
    WHERE Tracks.album_id = albums.id
    AND albums.title = 
      $1`, [album] ) // if no callback specified, then blocks as below
      .then(response => {
        callback(null, response.rows)
      })
      .catch(error => {
        callback(error)
      });
      
    }

    tracksofAlbum("Cowboy Bebop",  function(err, output) {
      if(!err) {
        console.log("Track found", output);
      } else {
        console.log(err);
      }
    });

    return {
      tracksofAlbum: tracksOfAlbum,
      firstTrackOfAlbum: firstTrackOfAlbum,
      titleofalbum:titleofalbum
    }

  })()

  const musicdb = require ('.live')

  ```
  * client.end() within only disconnects once callback is complete, if another query is called subsequently,
  as long as the first query not finished, it would work

  * SQL injection is the most common type of security threat in web applications

  * Select tracs.title from tracks, albums
  WHERE Tracks.album_id = albums.id
  AND albums.title = 
    
  * Write as many of these functions as we need
  * Objective is to have one function for every possible piece of data we need from the database
  * List of albums
  * Get all albums
  * If know albums, get all tracks
  * If know tracks, get all details
  * etc. 
  * Application only cares about the functions, not how the database is working
  * Organize this code as a library
  * Require the whole thing, and just use it

## Breakout Notes

* knex
  * why?
    * Have sqlite in development but postgres in production
    * knex allows you to write in a common language that talks to all of them
    * Today set up computers to be as similar as possible to production
    * 


  * examples
    * postgres vs sqlite



* Seeding
  * Practice of maintaining one or multiple files in project
  * Write code so that we can add fake data (seed database with fake data)
  * Maintain one type of seed data to put in
* Migrations
  * Code changing over time
  * Data changes over time also
  * User, songs and likes
  * Change the schema
  * Migration keesp data in sync
  * Any time to make change to database, instead of directly going to database, 
  write it into a *new* "migration file"
  * it includes the changes (alter table...)
  * Changes include up or down step, for do and undo 
  
  knex migration:new create-starting-tables
    migrations/2019-01-12-create-alltables
  knex migration:new add-email-to-user
    migrations/2019-04-23-14091929-add-email-to-user.js

  * commit these files to gitproject
  * never edit previous migrations, only append to it
  * 
  * Apply to database
  
  knex migrate:latest
  knex migrate:rollback
  knex drop; knex migrate:latest, knex seed // never do this in production

  * At any point in project, recreate database and it will work with the app

* Production system
  * Development database and production database
  * This tooling helps with that, shows what steps are needed in development
  * Apply the same steps to production
  * Migrate:latest

* Migrations is something we will want to do in midterms

* Pooling
  * Knex is maintaining multiple connections
  * Make parallel requests by allowing pool 

``` javascript
var query = db.select("name") .from("artists");

console.log(query.toSQL().sql); // inspect what query actually didi

query.then(function(results) {  // trigger the query to run
  console.log(results);
});

query.then(function(resutls) {
  return results.map(function(artist) {return artist.id});
}).then(function(ids) {
  return Promise.all(
    ids.map(function(id) {
      return db.select("title").from("albums").where({artist_id: id})
    })
  )
}).then(function(results){
  console.log(results);
}).catch(function(err){
  console.log(err);
})

/*
query.asCallback(function(err, results) {
  
  results.forEach( function(artist) {

    let q = db.select("name").from("albums") where({artist_id:artist.id});

    db.select("title").from("albums").where({artist_id: artist.id})
    .asCallback(function(err, album) {
      if (err) {
        console.log(err)
      } else {
        console.log(album);
      }
    })
  });
db.destroy(); -// tell knex to disconnect from the database, only need to do this for one time scripts
});
*/


// Use Promises, alternative syntax


