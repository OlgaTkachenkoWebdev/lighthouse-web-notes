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