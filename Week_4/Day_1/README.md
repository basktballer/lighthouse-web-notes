#Week 4 Day 1 Notes
## Lecture Notes

* SQL / Databases
  * Objective is to get into SQL
  * As software people, need to be come experts in the system that we are doing
  * Tell me everything you know and build the vocabulary
  * Typically this can happen as a conversation
  * Tell me everything you did yesterday
  * Identify key words, nouns
  * Pick the entity, branch out into descriptions of the entities 
  * Playlist, artist, album, genre
  * Analysis for database
  * ERD
    * Diagram that aligns the entities that the system will be able to handle
    * Only document needed to build a database
    * Be aware of how the entities are related to each other
    * Organize the data dictionary
    * Relationship of the artist to the album
    * Key to building a good system is to make up your mind when doing the ERD
    * Best place to establish the rules for building the system
  * SQL built with the only idea of doing data
    * If it knows what you want and how the data is structured, it can get the data out
  * Create table
    * Definition language
    * Artists
      * ID
      * Name
      * Foreign Key
  * SQL has it's own data types
    * VARCHAR(50) string of length 50
      * TEXT not needed to specify the length
      * Less efficient than VARCHAR, stored elsewhere
      * Used for Blog posts
    * id SERIAL PRIMARY KEY NOT NULL // Serial means that ID increments 
    * alubm_id INTEGER NOT NULL REFERENCES album(id) ON DELETE CASCADE
    * Foreign Key singular name to tables linked
    * SQL is one of the languages that has been around since the beginning
    * If you invest a little time to learn it, chances are you will be seeing it again in the future

  * vagrant
    * psql // already installed
    * name of db at this point shown
    * \l to show all databases on this server
    * in a relational database need to decide the shape of the entity
    * different than mongoDB
    * use vagrant
    * \dt to show all tables in the selected database
    * select * from tags

    * INSERT INTO "tags" (id, name) VALUES(1, 'post-rock');
    * select * from tags
    * select name from tags
    * where name like 'e%'; // split multiple lines if don't use semi-colon
    * \e goes to VI editor, modify the command and runs the command when done
    * SLECT * from albums, tracks where albums.id = tracks.album_id and albums.title = 'Cowboy Bebop';

    * SELECT
      tracks.title AS title,
      albums.title AS album,
      artist.title as artist,
      FROM tracks, albums, artists
      WHERE albums.artist_id = artists.id
      AND tracks.album_id = album.id


    * SELECT 
      tracks.title AS title,
      albums.title AS album,
      artist.name AS artist
      FROM tracks
      JOIN albums ON tracks.album_id = albums.id
      JOIN artists ON albums.artist_id = artists.id
    
    * SELELCT
      artists.name AS artist,
      string+agg(tags.name, ', ') as tag,
      count(*)
      FROM artists, tags, artists_tags as at 
      WHERE at.artist_id = artists.id
      AND at.tag_id = tags.id
      GROUP BY artist;

    * SELECT * FROM tags;
    * select * from artists_tags
      where tag_id = 5;
    * select * from artists where id = 5;

    * select tags.name, count(*) 
      from artists_tags, tags, artists
      where artists_tags.tag_id = tags.id
      and artists_tags.artist_id = artists.id
      group by tags.name

## Breakout Notes

* New SQL statements
* EXPLAIN ANALYZE 
  * See the query plan
* Explain that data is there, stored as a hard drive in a concrete structure
* Use knowledge of how data is storede
* Complex Queries
* Take the time to learn it to run the query and get the result in one query
* Spend some time to learn the proper query needed
* When doing AND with OR nested, use brackets
* 

       