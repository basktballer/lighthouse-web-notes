#Week 2 Day 3 Notes
## Lecture Notes

* How to frame server requests and what it looks like? 
  * Server can return JSON, could return files, pictures, movies, XML
  * Today focused on HTML
  * Different views populated
  * REST (Representational State Transfer)
    * /nouns (/posts)
    * /nouns/verbs (/posts/create)
    * /nouns/verbs/id (/posts/1234, /posts/1234/edit, /posts/1234/comments)
    
  * CRUD
    * Create, read, update deleete

  * BREAD
    * Brows, read, edit, add, delete
    * Browse to /post/id (GET/POST)
    * /post/id/ (SHOW request to)
    * Edit -> Expect a form, same as Add but have limited fields (PUT/PATCH/POST)
    * Add -> Expect a form
    * Delete -> DELETE request, not common. GET form and DELETE

* If into front end, need to keep up to date. 

* Difference between express and react
  * Framework is a bunch of freebies, compiles back to a base language
    * ie. Ruby on Rails
  * React is a front end framework, transpiled back to older frameworks
  * www.caniuse.com
    * arrow function check compatibility
  * Express is a framework for backend
    * Server side
  * Node allows js to run on serverside
  * React for the most part is a browser framework for client side javascript

* Build a server
  * Express generator
  * get nvm, node version manager. allows for different versions of node
  * npm install -g express-generator
    * g for global
  * express -e petbook
  * Command D to select all
  * Replaced all const to var
  * index.js in routes folder
    * Create an object called pets database
    * Create a new route to show all pets
    * View associated with all that
    * Index View
  * Show one pet
  * Add new pets
  * Edit existing pet
  * Delete pet
  * Doing cookies today and will learn trick
  * const findPet = id => petDB.find(pet => pet.id === Number(id)); // find is an iterator, look through each item pet, and check pet.id === id
  * const findPetIndex = id => petsDB.findIndex( pet => pet.id === Number(id)); // 
  * router.get('/pets/:id', (req, res) => {
    const { id } = req.params; // es6 object destructuring, match variable name with keys inside object passed to it
    const findPet = id => petDB.find(pet => pet.id === Number(id)) // find is an iterator, look through each item pet, and check pet.id === id
    res.render('show', {pet: findPet(id)})
  })

  * only POST in a form, no other methods
  * Edit in the POST
    * router.get('/pets/:id/edit', (req, res) => {
      const { id } = req.params;
      const petToEdit = findPet(id);

      res.render('edit', {pet: petToEdit});
    })
    * router.post('/pets/:id/edit', (req, res)=> {
      const {
        id, 
        name, 
        imgURL
      } = req.body;

      const updatedPet = {
        id: Number(id),
        name,
        imgURL
      };
      
      petsDB[(findPetIndex(id)] = updatedPet;
      res.redirect(`/pets/${id}`)

    });
    * <input type ="hidden" name="id" value="<%= pet.id.name %>">
  * Add a new 
    * Post to /pets
    * router.post('/pets', (req,res) => {
        const id = petsDB.length + 1;
        const { name, imgURL} = req.body;

        const newPet = { // structure into variable called new pet, typically want to do some validations before pushing into the DB
          id,
          name,
          imgURL
        }

        petsDB.push(newPet)
        res.redirect('/pets')
    })
  * GET for a Delete
    * router.get('/pets/:id/delete', (req, res) => {

      const { id } = req.params;
      petsDB.splice(findPetIndex(id), 1);
      res.redirect('/pets);
    }) 

* Tips
  * Tools used, terminal is hyper. iTerm replacement
  * Use VS Code for text editing, run terminal from vscode
  * Placekittens.com with width and height
  * Placecage.com with width and height
  * Object.freeze around attributes 
  * Accessibility, 13% suffer from visual impairment
    * Always have an image with an alt tag
    * Don't have an a tag without a title
  * Need a unique identifier in a db, don't use username or email
  * Command control space on mac to get emoji short cuts, github supports emojis