## Concatenation
operation of joining character strings end-to-end

## Method
Is a function that applies to a variable
## Hoisting
Hoisting is JavaScript's default behavior of moving declarations to the top.
## Template literal
```
`${name}`
```
## Notation
In JavaScript, one can access properties using the dot notation (foo.bar) or square-bracket notation (foo["bar"])
## Function declaration(function definition, function statement)
* Hoisted

```JavaScript
function sayHello()
```
## Function expression(invoke the function, call the function)
* not hoisted
```JavaScript
const sayHello = function(name) {}
sayHello("Ozzy");
```
## Coersion
The process of automatic or implicit conversion of values from one data type to another. This includes conversion from Number to String, String to Number, Boolean to Number etc.
```
Alice + 2 = Alice2
```
## Callback function
is a function that we pass to another function as an argument
## Higher order functions
are functions that accepts another function as an argument or function that returns another function
## Anonymus
= without a key
## Literal
JavaScript Literals are constant values that can be assigned to the variables that are called literals or constants. JavaScript Literals are syntactic representations for different types of data like numeric, string, Boolean, array, etc data.

Types of JavaScript Literals
* Integer Literals
* Floating Number Literals
* String Literals
* Array Literals
* Boolean Literals
* Object Literals

## Explicit Return
A function is returned values using the return keyword, it’s called an explicit return.
## Implicit return
A function is returned values without using the return keyword, it’s called an implicit return.
## API
Application Programming Interfaces (APIs) are constructs made available in programming languages to allow developers to create complex functionality more easily. They abstract more complex code away from you, providing some easier syntax to use in its place.

## paginated
an ordinal numbering of pages, which is usually located at the top or bottom of the site pages. API pagination just applies that principle to the realm of API design.

Pagination helps to limit the number of results to help keep network traffic in check.
## Equal, deep equal, strict equal
`Assert.equal` works the same as using a double equals in JavaScript. This means that you get value checking, and JavaScripts fancy type conversions kick in.

`Assert.strictEqual` works just like the triple equals in JavaScript. This means that you get strict comparison checking both value and type.

Both methods check complex objects by reference, not value. That is where `deepEquals` comes in. `deepEquals` check objects and their properties for value equality:
```js
assert.deepEqual({n:1}, {n:1});    //true
assert.deepEqual({n:1}, {n:true}); //true
assert.deepEqual({n:1}, {n:"1"});  //true
```
`deepEquals` does a == comparison of type and value for nested properties and child objects of complex objects.

## Deep copy
A deep copy of an object is a copy whose properties do not share the same references (point to the same underlying values) as those of the source object from which the copy was made. As a result, when you change either the source or the copy, you can be assured you're not causing the other object to change too

## Shallow copy
The shallow copy of an object refers to the reference location/address of the original object. In case any field of the object reference to the other objects, it copies only the reference address (i.e., the memory address) of the object and no new object is created.
## API
Application Programming Interface
## DNS
Domain Name System
## URL
URL stands for Uniform Resource Locator. A URL is simply an address allocated to a resource on the web. This resource can be in form of an HTML webpage, an image, CSS file, etc.
## TCP
Transmission Control Protocol, provides a standard that allows machines to speak to each other.