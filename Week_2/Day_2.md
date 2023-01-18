## Event Handling and User Input

```js
const stdin = process.stdin;
// don't worry about these next two lines of setup work.
stdin.setRawMode(true);
stdin.setEncoding('utf8');

stdin.on('data', (key) => {
  process.stdout.write('.');
  if (key === '\u0003') {
    process.exit();
  }
});

console.log('after callback');
```
Here we're using `process.stdin` as well as **process.stdout**. As you may have guessed, `stdin` deals with "standard input", much like how `stdout` is for "standard output".

We use the on method on `stdin` to register a callback. Unlike `setTimeout`, this callback is not scheduled to run x seconds later. No delay information is provided for this reason. Instead, it is meant to run any time the user provides input to the program. In our case, our callback function, which is called each time there is new user input data, simply prints a "." to the screen.

As for the `"after callback"` output, this executes before any input. This is because `on` returns immediately, without running the callback code. It's job isn't to run the callback right away, but rather save it for later. In that way, it's similar to `setTimeout`, isn't it?

In order for this to actually work, there's a few more lines of code to setup stdin properly. These configuration settings are not important to our learning of asynchronous programming right now, so we won't focus on them.

## Readline

Read the important parts of the [documentation for readline](https://github.com/nodejs/node/blob/main/doc/api/readline.md)

Focus on the following:

* The example usage shown at the beginning
* The .question(query, callback) function
* The .close() function
Instruction

```js
const readline = require('readline');

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question('What do you think of Node.js? ', (answer) => {
  console.log(`Thank you for your valuable feedback: ${answer}`);

  rl.close();
});
```

## Intro to net
```js
// server.js
const net = require("net");
const server = net.createServer();
server.on("connection", (client) => {
  console.log("New client connected!");

  client.write("Hello from the server!");

  client.setEncoding("utf8"); // interpret data as text

  client.on("data", (data) => {
    console.log("Message from client: ", data);
  });
});
server.listen(3000, () => {
  console.log("Server listening on port 3000!");
});
// client.js
const net = require("net");
const conn = net.createConnection({
  host: "localhost",
  port: 3000
});
conn.on("data", (data) => {
  console.log("Server says: ", data);
});
conn.on("connect", () => {
  conn.write("Hello from client!");
});
conn.setEncoding("utf8");
```
Here we have the foundation of how an app can "call up" another app. The client is always the one establishing the connection to the server. All the client needs is the destination IP address and PORT information.
