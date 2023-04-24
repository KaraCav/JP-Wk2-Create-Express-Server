# Week 2 Code Along: Create an Express Server

## Part 1 - Setup
Use `mkdir` to create a new folder. `cd` into the empty folder.

1. Run `npm init -y` to initialize Node in your project folder. The -y indicates a “yes” for all options - it creates a package.json for you.
2. With package.json open, run `npm i express` (see pkg added)
    a. This creates a package-lock and node modules
3. We will use Nodemon, but it isn’t needed for the project to run. Install it as a dev dependency w/ `npm i —-save-dev nodemon`
    
    a. Nodemon restarts the Node server every time we make a change
4. To get nodemon to start, use `npm run nodemon filename.js`
    
    a. Remember, we used to need to type `node filename` every time
    
    b. We can make a script to use instead by adding a ‘scripts’ property to the package.json. That will look like this:    
        ```
        "scripts": {
        	"start": "nodemon server.js"
        } ```
5. It will want to run a file called server.js, so we need to make that in our root directory.

## Part 2 - Creating the Server
1. Test that the setup was correct by adding a console.log to server.js. run `npm run start` . Change the message and save to see the update.
2. Node uses require. Start by requiring ‘express’ in our file  
    `const express = require('express');`
3. Calling express as a function creates the express application
    
    ```const app = express(); ```
    
4. Make the app listen → `app.listen(3000)` and open localhost:3000
    a. [localhost](http://localhost) always points back to your own machine - can’t see someone else’s
    b. It will show a “cannot GET / “ message - looking for a route to hit
    c. This is a built-in Express error saying 'I don’t see that route!'
5. Write a route! → `app.get(’/’, (req, res, next) ⇒ {  } )`
   
   a. .get() takes in a path, in this case the root directory '/', and a function   
        ``` app.get('/', (req, res) => {
            res.send("Hello again");
        }) // page will change to say 'Hello again'
        ```
    b. req,res,next are parameters, but don’t often use next
    
6. Send a response. res.send() is the most basic - returns what we sent to the browser
  - Try sending a status - res.sendStatus(200) vs. (500)
     - res.status will show in the browser console - in Network, click on the [localhost](http://localhost) file - it will show the status (is red if sent a 400)
  - Can chain together, like res.status(200).send(”hi”), or .json( {msg: “it works”} )
  - most commonly, we’ll use res.render and return a page view (HTML code/file)
 ```res.send("<h1>Hey friends, this is big text!</h1>")```
