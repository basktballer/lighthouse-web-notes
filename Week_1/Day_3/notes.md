#Week 1 Day 3 Notes
## Lecture Notes

* Objects
  * Keys are always strings
  * object["key"] to access values
  * object.key also to access values

* When a object is passed to a function, it passes the pointer to the where object is stored memory
  * Object passed to functions by reference as opposed to by copy ( for primitive values )
  * When it changes in a function, it is changed in the global scope also
  * function replace(ref) {
  ref = []; // this code does not affect object passsed, creates new array called ref. Same with objects also.

  ref.push(1); // this does affect ref
}


## Excercises
* Social Network
  * Refactor the Social Network exercise
    * If Else or If, Else If, Else
      * Good practice is to end with Else

  * Use Underscore to try to simplify functions
    * Use Map?

  * Follows who?
  * List of Followers
  * Most followers
  * Most followers > 30
  * Follows most > 30
  * Follow someone that doesn't follow back
  * Everyone and reach (sum of followers & followers of followers)

.