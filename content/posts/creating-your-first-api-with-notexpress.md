---
title: Creating your first API with NotExpress
date: 2022-03-27T09:00:00Z
tags:
  - notexpress
categories: life
keywords: 
---


You have probably heard of Express.js. But have you heard of NotExpress.js? I don’t think so. Today, I am going use the Express.js knock-off I built to teach you how to use it to build a RESTful API. If you want to read my motivations for building yet ‘another JavaScript’ framework, check _this article out_.

## Prerequisites
I am assuming that you have some knowledge of the aforementioned, in order to fully benefit from this guide.

- Command line usage
- Basic JavaScript
- Basic Node.js and npm
- Minimum understanding of RESTful APIs
## Setting up our project
First of all, create a new folder and navigate into it. Initialize a new Node project as below.
```Bash
$ npm init -y
```

A new file named _package.json_ will be created. Because the command was executed with the _-y_ flag, the file will be created with default configuration.
## Install NotExpress
Having initialized your project, you may proceed and install NotExpress
```Bash
$ npm install @ndimz/notexpress
```
You might also want to install _nodemon_ as a dev dependency. It automatically reruns your node source every time you make a change.
```Bash
$ npm install --save-dev nodemon
```
But for simplicity sake, the tutorial will not cover its usage.
## Creating a very simple endpoint
We are now ready to start coding your first NotExpress application. We’re first going to create a basic Hello World program. This program will respond with some data when a request is sent to the defined endpoint. Create a file in the project directory and name it _helloworld.js_. This is requiring the _@ndimz/notexpress_ module and creating our _app_ instance as well as the _port_ for our server.
```Javascript
const notexpress = require("@ndimz/notexpress");
const app = new notexpress();
const port = 3000;
```
So now we can create our <b>GET</b> endpoint to send back <b>Hello World!</b>. We will use the home page, <b>/</b>.
```Javascript
app.get("/", (req, res) => {
  res.end("Hello World!");
});
```
Now the endpoint is set, we need to setup our listen to listen on our defined port.
```Javascript
app.listen(port, () => {
  console.log("Server running on port ${port}");
});
```
We can now start our server by executing our <b>index.js</b> file.
```bash
$ node index.js
```
If you are using an <b>HTTP Client</b> like Postman or any browser, visit the URL <b>http://localhost:3000</b> and you will see the response.
Our <b>helloworld.js</b> should look like this:
```Javascript
const notexpress = require("@ndimz/notexpress");
const app = new notexpress();
const port = 3000;

app.get("/", (req, res) => {
  res.end("Hello World!");
});

app.listen(port, () => {
  console.log("Server running on port ${port}");
});
```
## Adding a new user
Now that we have created our “Hello World” program, create a new file called <b>index.js</b>. We will start building our application in this file.
```Javascript
const notexpress = require("@ndimz/notexpress");
const app = new notexpress();
const port = 3000;

// our user storage
let users = [];

app.post("/", (req, res) => {
  const user = {
    id: users.length + 1,
    name: req.body.name,
    age: req.body.age,
  };

  users.push(user);
  res.send("User added successfully");
});

app.listen(port, () => {
  console.log("Server running on port ${port}");
});
```
We created a new global variable named <b>users</b>. This is going to act as if it is our database.

If you are familiar with Express, you will notice that there is no call to configure HTTP Request body parsing. This is done by default in <b>notexpress</b>. Within the <b>app.post()</b>, we added a new user from the data gotten from the request.
## Retrieving all users
We will create another endpoint to be able to get all the users from our API. You have to manually stop the server and start it again for the changes to take effect.
```Javascript
app.get("/users", (req, res) => {
  res.status(200).json({
    data: users,
  });
});
```
<b>res.status()</b> method returns the <b>response object</b>. This is why we can chain the <b>json()</b> method to respond back with all the users.
## Getting a single existing user
To be able to get a single user provided with their ID, we will set another endpoint with a dynamic route. If the request <b>URL</b> matches the pattern defined in our API, and the ID exists, we will respond with the user.
```Javascript
app.get("/user/:id", (req, res) => {
  const id = req.params.id;
  let user = users.find((usr) => usr.id == id);

  if (user) {
    res.status(200).json({
      data: user,
    });
  } else {
    res.status(404).json({
      message: "User with that ID not found",
    });
  }
});
```
Any request with a URL pattern of <b>/users</b> followed by anything, will hit this endpoint. The preceeding value is stored in an <b>id</b> variable. After looking for the user from the array, we send back a response depending on the availability of the searched user.
## Conclusion
The rest of the other HTTP Methods can be implemented in a similar way.
Take it upon yourself to try implementing them as practice. NotExpress is nice, isn't it?


Be sure to check out the framework source code [on GitHub](https://github.com/ndimzKM/notexpress) to add your contributions. They are highly welcomed.
  
