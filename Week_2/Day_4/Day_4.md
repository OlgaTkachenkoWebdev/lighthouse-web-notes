# JSON
JSON is built on two structures:

* A collection of name/value pairs.
* An ordered list of values.

The process of `serialization` converts objects (or data structures) into a format that can be stored or transmitted between computers (typically as a string of text). The opposite, going from String → Object is called `deserialization`.

## JSON.parse()
Parse a string as JSON, optionally transform the produced value and its properties, and return the value.

## JSON.stringify()
Return a JSON string corresponding to the specified value, optionally including only certain properties or replacing property values in a user-defined manner.

## JSON Media Type
When data is sent across the web using HTTP request/responses, the Media Type for JSON data is application/json (compared to text/html for HTML). It is set via the Content-Type HTTP response header.

# API
In the simplest terms, APIs are sets of requirements that govern how one application can talk to another.

# Promises
* A promise is an object
* Promises do not rely on anything other than basic JavaScript
* As of ES6, JavaScript has promises supported natively in its code. In other words, they are built into the language (via Promise)
```js
gotoTheirHouse(billy)
  .then(pretendToBeFriends)
  .then(stealWhenNotLooking)
  .then(hideInBackpack)
  .then(() => {
    console.log("I don't feel well. I gotta go home now Billy!");
  });
  ```
  Example
  ```js
  let creditLimit = 300;
  /*
 * Input: number of dollars to loan out
 * Returns: Promise of loan which may or may not fulfill, based on remaining credit. 
 * If creditLimit is less than the requested amount, only the remaining limit is loaned out, otherwise the full amount is loaned out. If $0 remain in the limit, the loan request is rejected (error!).
 */

const loanOut = function(amount) {
  return new Promise((resolve, reject) => {
    /* a promise needs two callback functions, one for success (resolve) and one for failure (reject).
    */
    if (creditLimit <= 0) {
      reject("Insufficient Funds!");
    } else if (creditLimit > 0 && creditLimit < amount) {
      amount = creditLimit;
      creditLimit -= amount;
      resolve(amount)
    } else { 
      creditLimit -= amount;
      resolve(amount);
    }
  });
};

loanOut(5050)
  .then((amountReceived) => {
    console.log(`\t-> I got $${amountReceived} loan from the bank! Remaining Credit Limit: $${creditLimit}`);
  })
  .catch((err) => {
    console.log(`\t-> Error: ${err}!`);
  });
  ```