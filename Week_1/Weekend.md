```javaScript
//in parent folder
npm init
npm install mocha@9.2.2 chai --save-dev 
// in package.json
"scripts": {
    "test": "./node_modules/mocha/bin/mocha"
  },

// create test folder, make test.js file here
Our directory structure should now look like this:
|__folder
   |-file.js
   |-test_folder
     |__test.js

npm test

const assert = require("chai").assert;
const isPalindrome = require("../lib/palindromes");

const sayHello = require("./hello-world");
const chai = require('chai'); // so we can use assert
const assert = chai.assert;

assert.equal(sayHello("tony"),"hello tony!!"); //assert.equal(actual, expected) built in node, but we need to define assert at the beginning

module.exports = isPalindrome;

const ii = 66;

if (ii < 10) {
    console.log("ii:",ii);
} else {
    throw new Error('arbitrary error text goes here!');
}
assert.throws()