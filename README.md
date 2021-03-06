## Steps to create a backend in NodeJs + Express:
_Please clone this repository and follow the below instructions in the cloned folder in your computer:_

### Prerequisites:
- Install Node (https://nodejs.org/en/download/)

### Simple steps to create the boilerplate package:
1. Create the package.json:
   - `npm init` and `npm install --save express body-parser`
   - OR create a new file named `package.json` and paste:

```json
{
  "name": "postman-generated-backend",
  "version": "1.0.0",
  "description": "Backend app generated via Postman",
  "main": "index.js",
  "scripts": {
    "start": "node server.js"
  },
  "author": "user",
  "license": "ISC",
  "dependencies": "{\n    \"body-parser\": \"^1.19.0\",\n    \"express\": \"^4.17.1\"\n}"
}
```

2. Create `server.js`:
   - Create a new file named `server.js` and paste:

```javascript
const express = require("express");
const bodyParser = require("body-parser");

const app = express();

// parse requests of content-type - application/json
app.use(bodyParser.json());

// parse requests of content-type - application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: true }));

// simple route
app.get("/", (req, res) => {
  res.json({ message: "Welcome to your backend app" });
});
require("./app/routes/index")(app);

// set port, listen for requests
const PORT = process.env.PORT || 8080;
app.listen(PORT, () => {
  console.log(`Server is deployed and running on port ${PORT}.`);
});
```
3. Create new folders :
    - `app`
    - `app/routes`
    - `app/controllers`
3. Create the router
    - In `app/routes`, create a new file `index.js` and paste the following in it:

```javascript
module.exports = (app) => {
  const controller = require("../controllers/api.controller.js");

  var router = require("express").Router();

    router.post("/", controller.createItem);

            

  app.use("/v1/", router);
};

```
4. Create the controller
    - In `app/controllers`, create a new file `api.controller.js` and paste the following:

```javascript


            exports.createItem = (req,res) => {
            //TODO: Add code for implementation

            res.status(200).send({
        message: "Endpoint to be implemented"        
    });

            

}

```

### Steps to run:
1. After creating all the files as instructed above, open terminal and `cd` to the project folder.
2. Enter the command- `npm install`
3. Enter the command  `npm run start`
4. Your app should start running on port 8080
5. Develop your app and test on Postman! :)

Thank you!
Created by: https://github.com/sank20, Generated by **you** <‰
