# How JS Actually Works
[Video](https://youtu.be/6MXRNXXgP_0) 
# Promises
By default Javascript uses callbacks to handle asynchronous work. This is when you parse a function into another function as an argument.

Using callbacks, it is hard to handle errors. It also becomes harder to follow the sequence. Take a look at the example code snippets below.
```js
function loadImage (src, parent, callback){
   let img = document.createElement('img')
   img.src = src
   img.onload = callback
   parent.appendChild(img)
}

// Pyramid Of Doom with callbacks

loadImage('above-the-fold.jpg', imgContainer, function(){
   loadImage('just-below-the-fold.jpg', imgContainer2, function(){
       loadImage('farther-down-the-fold.jpg', imgContainer3, function(){
           loadImage('abstract-art.jpg', imgContainer4, function(){
               loadImage('last-one.jpg', imgContainer5)
           })
       })
   })
})
```
With Promises, it becomes a lot easier to read.
```js
const sequence = get('example.json')
.then(doSomething)
.then(doSomethingElse);
```
## There are four stages in creating Promises:

1. Wrapping (syntax, or the Promise structure)

2. Thening (when it works)

3. Catching (recovery, when there's an error)

4. Chaining (where you create long sequences of asynchronous work)

## And, there are four states of a Promise:

1. Fulfilled (it worked!)

2. Rejected (failed)

3. Pending (still waiting...)

4. Settled (something happened)


### Promises execute in the main thread, meaning they are still potentially blocking.
```js
 new Promise(function (resolve, reject){
   resolve('hi') // works
   reject('bye') // can't happen a second time
})
```
## Syntax
```js
new Promise(function (resolve, reject){
   const value = doSomething()
   if (thingWorked){
       resolve(value)
   } else if (somethingWentWrong) {
       reject()
   }
})
.then(function(value){
   //success
   return nextThing(value)
})
.catch(rejectFunction)

new Promise(function (resolve, reject){
   let img = document.createElement('img')
   img.src = src
   img.onload = resolve
   img.onerror = reject
   document.body.appendChild(img)
})
.then(finishLoading)
.catch(showAlternateImage)
```

## Here are two ways to handle errors.
* Using a .catch
```js
get('example.json')
   .then(resolveFunc)
   .catch(rejectFunc)
```
* Chaining a second .then to handle the error
```js
get('example.json')
   .then(resolveFunc)
   .then(undefined, rejectFunc)
```
You can’t call both the resolve and the reject function in the same `.then`

# Domain Name System
[Video](https://youtu.be/72snZctFFtA)

## Record Types
Although there are many available DNS Record Types, there is a small subset that cover most use cases.

* A: most common; map a hostnames to IP address (IPv4, 32-bit address)
* NS: Name Server that is responsible for a DNS zone
* MX: Mail Exchange record specifies where email gets sent to
* CNAME: Canonical Name, an alias for another hostname
* AAAA: similar to A, but uses IPv6, 128-bit address


# Express
The express framework is the most common framework used for developing Node js applications. The express framework is built on top of the node.js framework and helps in fast-tracking development of server-based applications.
```js
var express = require('express'); //using the require function to include the “express module.”
var app = express(); //Before we can start using the express module, we need to make an object of it.
app.get('/',function(req,res) //Here we are creating a callback function. This function will be 
//called whenever anybody browses to the root of our web application which is http://localhost:3000 .
// The callback function will be used to send the string ‘Hello World’ to the web page.
{
res.send('Hello World!'); //n the callback function, we are sending the string “Hello World” back to 
//the client. The ‘res’ parameter is used to send content back to the web page. This ‘res’ parameter 
//is something that is provided by the ‘request’ module to enable one to send content back to the web page.
});
var server = app.listen(3000,function() {}); //We are then using the listen to function to make our server 
//application listen to client requests on port no 3000. You can specify any available port over here.
```
Routing

```js
var express = require('express');
var app = express();
app.route('/Node').get(function(req,res) //Here we are defining a route if the URL http://localhost:3000/Node 
//is selected in the browser. To the route, we are attaching a callback function which will be called when we 
//browse to the Node URL.The function has 2 parameters.
//The main parameter we will be using is the ‘res’ parameter, which can be used to send information back to the client.
//The ‘req’ parameter has information about the request being made. Sometimes additional parameters could be sent as 
//part of the request being made, and hence the ‘req’ parameter can be used to find the additional parameters being sent.
{
    res.send("Tutorial on Node"); //We are using the send function to send the string “Tutorial on Node” back to 
    //the client if the Node route is chosen.
});
app.route('/Angular').get(function(req,res) //Here we are defining a route if the URL http://localhost:3000/Angular 
//is selected in the browser. To the route, we are attaching a callback function which will be called when we browse 
//to the Angular URL.
{
    res.send("Tutorial on Angular");
});
app.get('/',function(req,res){
    res.send('Welcome to Guru99 Tutorials'); //This is the default route which is chosen when one browses to the 
    //route of the application – http://localhost:3000. When the default route is chosen, the message “Welcome 
    //to Guru99 Tutorials” will be sent to the client.
});
```

```js
const express  = require("express"); // Import the express library
const app = express(); // Define our app as an instance of express
const port = 3000; // Define our base URL as http:\\localhost:3000

app.get("/", function(req,res){ //tells our server that the GET function 
//is what we want people to do at this endpoint.
  res.send("Hello World!");
});

app.listen(port, function () {
  console.log(`Server running on port ${port}`); // Tell yourself the port number to prevent mistakes in the future.
});
```
