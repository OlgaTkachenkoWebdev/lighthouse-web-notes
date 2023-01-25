# HTTP

* HyperText is the HT in HTTP and HTML, and its origins date back to the 1960's.

* HTTP is a protocol used to read and write "resources" (data) in a simple text-based manner.

## HTTP flow
When a client wants to communicate with a server, either the final server or an intermediate proxy, it performs the following steps:

1. Open a TCP connection: The TCP connection is used to send a request, or several, and receive an answer. The client may open a new connection, reuse an existing connection, or open several TCP connections to the servers.
2. Send an HTTP message: HTTP messages (before HTTP/2) are human-readable. With HTTP/2, these simple messages are encapsulated in frames, making them impossible to read directly, but the principle remains the same. For example:
```js
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```
3. Read the response sent by the server, such as:
```js
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html>… (here come the 29769 bytes of the requested web page)
```
4. Close or reuse the connection for further requests.

* HTTP requests must contain the verb/method (eg: GET) and the Path (eg: /about)
* HTTP requests aren't always to receive data, but sometimes to save data, like when we submit a form on a website. This is done via a POST instead of a GET
* Requests and responses both contain key-value based headers (eg: Accept-Language: fr, Content-Type: text/html, etc.)

## Simple HTTP Example using net
```js
/** 
 * SETUP
 * Our usual client setup code
 * Connect to example.edu website's HTTP server using our TCP library
 * HTTP servers typically run on port 80
 */
const net = require('net');
const conn = net.createConnection({ 
  host: 'example.edu',
  port: 80
});
conn.setEncoding('UTF8');
// Add in the following code to actually make a request once connected.
conn.on('connect', () => {
  console.log(`Connected to server!`);

  conn.write(`GET / HTTP/1.1\r\n`);
  conn.write(`Host: example.edu\r\n`);
  conn.write(`\r\n`);
});
/** 
 * HTTP Response
 * After request is made, the HTTP server should send us HTTP data via our TCP connection
 * Print the data to the screen, and end the connection
 */
conn.on('data', (data) => {
  console.log(data);
  conn.end();
});
```
## Request

Instead of using the net library, or even the built-in http library, we will find that using an npm package called request to make HTTP requests is much simpler.
The request module makes HTTP requests easy. Behind the scenes, it uses http which in turn uses net, in the way that we did recently.
```js
const request = require('request');
request('http://www.google.com', (error, response, body) => {
  console.log('error:', error); // Print the error if one occurred
  console.log('statusCode:', response && response.statusCode); // Print the response status code if a response was received
  console.log('body:', body); // Print the HTML for the Google homepage.
});
```
# Lecture
### What is networking?
- Communication between machines on a network

### What is a protocol?
- A defined standard for how requests and responses are sent between network devices

### The OSI Model
- **O**pen **S**ystems **I**nterconnection Model developed by the International Organization for Standardization (ISO)
- Conceptual model of how data is transmitted over a network

1. **Physical** - physical pieces of hardware
2. **Datalink** - how the physical device is connect to the network
3. **Network** - communication between devices over the network
4. **Transport** - splits up the network communication into ports (~65000 of them)
5. **Session** - establishes a session between two connected devices
6. **Presentation** - data translation layer (encryption and decryption)
7. **Application** - the application (client or server)

### TCP/IP Model
1. **Network Access** - physical devices and how they connect to the network
2. **Internetwork** - communication between devices on the network
3. **Transport** - splits up the network communication into ports
4. **Application** - clients and servers/applications and services/sessions and encryption

### Transport Layer Protocols
- Break data into packets to be sent over the network layer
- Give each packet a header with origin and destination
- **UDP**: **U**ser **D**atagram **P**rotocol
  - Smaller header size (8 bytes) which results in smaller packet sizes
  - _Connectionless_ ie. there is no need to establish or maintain a connection
  - No error recovery (any corrupted packets are discarded)
  - Packets can arrive in any order
  - Useful for streaming/low latency applications
- **TCP**: **T**ransportation **C**ontrol **P**rotocol
  - Larger header size (20 bytes)
  - Requires a connection (3-way handshake)
  - Corrupted packets are reported to the server and are re-sent
  - Packets arrive in order
  - Useful when guaranteed communication is needed

### Useful Links
* [OSI Model](https://en.wikipedia.org/wiki/OSI_model)
* [Net package documentation](https://nodejs.org/api/net.html)