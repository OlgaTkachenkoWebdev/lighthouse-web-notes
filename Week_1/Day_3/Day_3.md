functions = objects

you can declare function inside function

## Arrow function
1. No `function` keyword
2. if only one argument, no parenthesis
3. If only one line of code, no curly braces
4. every arrow function has implicit return
5. Do not create `this`
```JavaScript
const sayHello = name => `hello there ${name}