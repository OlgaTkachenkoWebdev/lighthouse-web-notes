### Mocha
- A testing framework
- By default, looks in the `test` folder for test files to run

**Mocha** gives us the `describe` and `it` functions. Each `it` is a test, and each test should have at least **one** assertion.

### Chai
- An **assertion** library
- We can use _assertions_ to describe the desired outcome of our code
- Chai offers three different interfaces: `should`, `expect`, and `assert`
- For most uses, choosing which interface to use is a matter of preference

**Chai** is an assertion library. It gives us `assertion` functions so that we no longer have to use other assertion functions. Chai assertion functions are deliberately designed to play nice with testing frameworks like Mocha.

```javascript
// should
myVar.should.be.a('string');
myVar.should.equal('hello world');

// expect
expect(myVar).to.be.a('string');
expect(myVar).to.equal('hello world');

// assert
assert.typeOf(myVar, 'string');
assert.equal(myVar, 'hello world');
```

### `module.exports` and `require`
- We can export functions, objects, etc from a file using the `module.exports` object
- You can add new keys to the `module.exports` object _or_ you can completely overwrite it with a function/object
```JavaScript
// adding new keys to module.exports
module.exports.myFunc = myFunc;
module.exports.myOtherFunc = myOtherFunc;

// overwriting module.exports object
module.exports = myFunc;
// or
module.exports = {
  myFunc,
  myOtherFunc
};
```
- As you have previously seen, we can bring functions, objects, etc into a file using `require`
```javascript
// basic require syntax
const myFunc = require('./myFunc');

// if the file exports an object, we can use ES6 destructuring
const { myFunc } = require('./myFunc');
```
### Ignoring files/folders
- Sometimes there are files or folders that we do not want git to track for us
- These files might contain sensitive information such as passwords or API keys
- They might also be folders such as node_modules which should always be ignored
- We can tell git to ignore certain files/folders by using a special file called .gitignore (note the leading period)
- Any files that we specify inside of .gitignore will be ignored by git

```javascript
make .gitignore file.
add node_modules/ line to gitignore file
run this command 
git rm -r --cached .
git add .
git commit -m "remove gitignore files"
git push
```


### TDD
- **T**est **D**riven **D**evelopment
- Tests are written before the code is written
- We use a process called Red-Green-Refactor
- Red: The test is failing
- Green: The test is passing
- Refactor: Improve the existing code safe in the knowledge that the functionality is testable
- BDD: **B**ehaviour **D**riven **D**evelopment
  - Very similar to TDD, but the focus is more on the end user rather than the quality of the code under test




 ## Useful Links
- [Node Modules](https://nodejs.org/docs/latest/api/modules.html)
- [Node Wrapper Function](https://nodejs.org/api/modules.html#modules_the_module_wrapper)