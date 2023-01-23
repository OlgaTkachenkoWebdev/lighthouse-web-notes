# Simple OOP in JavaScript
```js
const dog = {
  sound: "woof",
  speak: function() {
    console.log(this.sound);
  },
  teachMeSomething: function() {
    if (dog === this) {
      console.log('dog === this');
    }
    this.speak();
  }
};

dog.teachMeSomething();
```
## Classes & Instances
To declare a `class`, you use the class keyword with the name of the class.
```js
class Pizza {
}
```
When you create an object using a class, it is an `instance` of that class.
```js
let pizza1 = new Pizza();
let pizza2 = new Pizza();
pizza1 === pizza2; // false
```
## Methods and Properties
You can add a `method` to a class with the following syntax:
```js
class SomeClass {
  methodName(parameters) {
    // this is a method
  }
}
```
To add `properties` to a class, simply use the this keyword followed by the property name, then assign it a value:

```js
class SomeClass {
  someMethod() {
    this.hello = "hi"; // Created a property called hello
  }
}
```

## Constructor
`Constructor` is a special kind of method that gets executed when an object instance is created from a class.
```js
class Pizza {
  constructor() {
    this.toppings = ["cheese"];
  }
}
```
# Inheritance
Perhaps we could remove this duplication by moving the shared code from two classes into yet another class. We are going to use a technique in OOP known as inheritance.

With inheritance, we can build a new class based on an existing class. 

```js
// This class represents all that is common between Student and Mentor
class Person {
  // moved here b/c it was identical
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }
  // moved here b/c it was identical
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}
```
```js
class Student extends Person {
  // stays in Student class since it's specific to students only
  enroll(cohort) {
    this.cohort = cohort;
  }
}

class Mentor extends Person {
  // specific to mentors
  goOnShift() {
    this.onShift = true;
  }
  // specific to mentors
  goOffShift() {
    this.onShift = false;
  }
}
```
# Super
A common need developers have to further share code between classes when using inheritance. The solution involves  special keyword `super`. In doing so, it also explores the concept of `method overriding`.

## Method Override
```js
// Superclass
class Person {
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}

// Subclass
class Mentor extends Person {
  // Completely re-define the bio method since it has more to say
  bio() {
    return `I'm a mentor at Lighthouse Labs. My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}
```
## Super
```js
// Super class
class Person {
  constructor(name, quirkyFact) {
    this.name = name;
    this.quirkyFact = quirkyFact;
  }
  bio() {
    return `My name is ${this.name} and here's my quirky fact: ${this.quirkyFact}`;
  }
}

class Mentor extends Person {
  // Mentor bios need to include a bit more info
  bio() {
    return `I'm a mentor at Lighthouse Labs. ${super.bio()}`;
  }
}
```
# Getters and Setters
Getters and setters are special methods that are used to get the value of a property or set the value of a property.

Let's go over two main reasons right now:

* Validating data before assigning it to a property
* Computing a value on the fly instead of simply pulling it out of a property
## Validating data
``` js
class Pizza {
  // setSize now includes data validation
  setSize(size) {
    if (size === 's' || size === 'm' || size === 'l') {
      this.size = size;
    }
    // else we could throw an error, return false, etc.
    // We choose here to ignore all other values!
  }
}

// DRIVER CODE
let pizza = new Pizza();
pizza.setSize('s');
```
## Computed value
```js
class Pizza {
  getPrice() {
    const basePrice = 10;
    const toppingPrice = 2;
    return basePrice + (this.toppings.length * toppingPrice);
  }
}

// DRIVER CODE
let pizza = new Pizza();
pizza.getPrice();
```
## Get and set
```js
class Pizza {

  // replace our custom getters / setters with these ones!
  get price() {
    const basePrice = 10;
    const toppingPrice = 2;
    return basePrice + this.toppings.length * toppingPrice;
  }

  set size(size) {
    if (size === 's' || size === 'm' || size === 'l') {
      this._size = size;
    }
  }
}
```
The only new things here are the get and set keywords in front of the getter and setter methods. The main difference we get from using these is that price and size will now be accessed as if they were value properties instead of method properties.
```js
let pizza = new Pizza();

pizza.price;      // instead of getPrice()
pizza.size = 's'; // instead of setSize(size)
```