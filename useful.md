## How can you empty an array in JavaScript?
There are actually a few methods to do this. Lets say you have the following array let array = [1, 2, 3, 4], you can empty it by:
```javascript
// creates a brand new empty array
array = [];

// clears the array without creating a copy
array.length = 0;

// modifies the array and returns the removed entries
array.splice(0, array.length);
```
## Explain the difference between `==` and `===`?
In JavaScript, there are two sets of equality operators. The triple-equal operator `===` behaves like any traditional equality operator would: evaluates to true if the two expressions on either of its sides have the same type and the same value. The double-equal operator, however, tries to coerce the values before comparing them. It is therefore generally good practice to use the `===` rather than `==`. The same holds true for `!==` vs `!=`.

## What are the six JavaScript data types?
- Boolean
- Number
- String
- Null
- Undefined
- Symbol

## What would be the result of 3+2+"7"?
Since 3 and 2 are integers, they will be added numerically. And since 7 is a string, it will resort to string concatenation, resulting in a string type. The result would be `"57"`.

## Explain JavaScript's for..in loop.
The for-in loop is used to loop through the properties of an object. More specifically, it loops through each key.

The syntax for the for-in loop is:
```javascript
for (let key in object) {
  // statement or block to execute for each key
}
```
In each repetition, one property from the object is associated to the variable (named key above), and the loop is continued until all of the properties of the object are depleted.