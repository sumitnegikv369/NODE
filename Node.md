## Node.js
- Node.js is an open-source, cross-platform JavaScript runtime environment.
- It allows developers to run JavaScript code outside a web browser, making it versatile for various applications.

## JavaScript Engine
A JavaScript engine is a program responsible for converting JavaScript code into machine code, enabling computers to execute specific tasks defined in JavaScript. One prominent JavaScript engine is V8, developed by Google and open-sourced for wider use. Node.js leverages the V8 engine, which is written in C++ and excels at handling lower-level operations efficiently.

## JavaScript Runtime Environment
A JavaScript runtime environment encompasses all the necessary components to use and run JavaScript programs effectively. These components include:
- **JS Engine**: Manages memory and the call stack, like V8 in the case of Node.js.
- **Web/Browser APIs**: Provides interfaces for interacting with web functionalities such as the Document Object Model (DOM), storage, and timers.
- **Event Loop**: Facilitates asynchronous operations through microtask queues and callback/task queues, crucial for non-blocking I/O operations in Node.js.

## Applications of Node.js
Node.js is versatile and empowers developers to build a wide range of applications, including:
- Traditional websites with dynamic content and server-side logic.
- Backend services like APIs for handling data exchange between clients and servers.
- Real-time applications such as chat apps or collaborative tools leveraging WebSockets for instant communication.
- Streaming services for media delivery and processing.
- Command-Line Interface (CLI) tools for automation and scripting tasks.
- Multiplayer games with real-time interactions and data synchronization.

## Node.js Components
Node.js relies on various components, with dependencies like the V8 engine playing a crucial role in its functioning. These components work together seamlessly to provide a robust environment for developing JavaScript-based applications.

## Node Modules
a module is a piece of reusable JavaScript code. It could be a .js file or a directory containing .js files. You can export the content of these files and use them in other files.

### HTTP module
The HTTP Module: A Core Library for Network Communication

- Type: Library
- Purpose: Enables Node.js applications to create web servers and make HTTP request/responses.
    
Servers:

- Created using http.createServer().
- Listen on a specific port (e.g., port 80 for standard web traffic).
- Handle incoming requests and send responses.

Requests and Responses:

- Requests represent incoming HTTP messages from clients, specifying the desired action (method) and resource (URL).
- Responses are sent back by the server, typically containing data (body) and status codes (e.g., 200 for success, 404 for not found).

Headers: Carry additional information about the request or response, such as content type, authentication credentials, or caching instructions.

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello from your Node.js server!');
});

server.listen(3000, () => {
  console.log('Server listening on port 3000');
});

```

### HTTP Status codes

 In Node.js, HTTP status codes are essential for communicating the outcome of an HTTP request-response cycle.
 Different types of status codes and their meanings:

1. **Informational Responses (100–199):**
   - These codes indicate that the server has received the request and is processing it. They are informational and don't typically affect the client's behavior.

2. **Successful Responses (200–299):**
   - These codes indicate that the request was successful. 
   Common ones include:
     - `200 OK`: The request was successful.
     - `201 Created`: A new resource was successfully created.
     - `204 No Content`: The server successfully processed the request but doesn't need to return any content.

3. **Redirects (300–399):**
   - These codes indicate that the client must take additional action to complete the request. Examples:
     - `301 Moved Permanently`: The requested resource has moved permanently.
     - `302 Found` (or `303 See Other`): Temporary redirection.

4. **Client Error Responses (400–499):**
   - These codes indicate that there was an error on the client side. Common ones include:
     - `400 Bad Request`: The request was malformed or invalid.
     - `401 Unauthorized`: Authentication is required.
     - `403 Forbidden`: The client doesn't have permission to access the resource.
     - `404 Not Found`: The requested resource does not exist.

5. **Server Error Responses (500–599):**
   - These codes indicate that there was an error on the server side. Examples:
     - `500 Internal Server Error`: An unexpected error occurred on the server.
     - `502 Bad Gateway`: The server received an invalid response from an upstream server.
     - `503 Service Unavailable`: The server is temporarily unable to handle requests.

These status codes helps clients understand the outcome of their requests and enables effective error handling.

In  Express.js, we can set status codes using `response.status(code)` and send corresponding messages. For example:
```javascript
response.status(200).send('OK');
response.status(404).send('Not Found');

```

## Built-in Core Modules
These come pre-installed with Node.js and are readily available for use in your projects.

- http: As you already learned, this module enables you to build web servers and make HTTP requests/responses.
- fs (file system): Provides functions for interacting with the file system, such as reading, writing, creating, and deleting files and directories.
- path: Helps in working with file and directory paths, including manipulation and normalization.
- os: Offers information and interaction with the operating system (OS) on which Node.js is running.
- process: Provides access to the current Node.js process object, including environment variables, command-line arguments, and process control.
- url: Used for parsing and working with URLs, including extracting components like protocol, hostname, and path.
- querystring: Assists in parsing and formatting query strings (the data appended to a URL after the ?) for use in web development.
- events: Provides a mechanism for handling events and creating event emitters (objects that can trigger and respond to events).

## Node.js global objects
1. dirname and __filename:

- __dirname: Represents the directory name of the current module. It gives you the absolute path of the directory containing the current module file.
- __filename: Represents the filename of the current module. It gives you the absolute path of the current module file.

```js
console.log(__dirname); // Outputs the directory path of the current module
console.log(__filename); // Outputs the file path of the current module
```

2. require:

- require is used in Node.js to include modules (files or packages) in your application.
- You can require your own modules by specifying the file path (./path/to/module) or use npm packages by specifying the package name.

```js
const fs = require('fs'); // Require the built-in 'fs' module
const myModule = require('./myModule'); // Require your own module
```

3. console:

- The console object in Node.js is used for logging messages to the console, debugging, and monitoring the application.
- Common methods include console.log(), console.error(), console.warn(), etc.

```js
console.log('Hello, world!'); // Log a message to the console
console.error('Error message'); // Log an error message
```

## Process Object
This object provides information and control over the current Node.js process, including details about the environment, command-line arguments, standard input/output streams, and various methods for interacting with the process.

1. Environment Variables (process.env):

- The process.env property provides access to the environment variables of the current process.
- You can use process.env to retrieve environment variables set in the system or by your application.

```js
const port = process.env.PORT || 3000;
```

2. Standard Streams (process.stdin, process.stdout, process.stderr):

- process.stdin: Represents the standard input stream. You can use it to read input from the user.
- process.stdout: Represents the standard output stream. You can use it to write output to the console or a file.
- process.stderr: Represents the standard error stream. You can use it to output error messages.

```js
process.stdout.write('Enter your name: ');
process.stdin.on('data', (data) => {
  console.log(`Hello, ${data.toString().trim()}!`);
  process.exit();
});
```

3. Process Information:

- process.pid: Returns the process ID of the current Node.js process.
- process.cwd(): Returns the current working directory of the Node.js process.
- process.argv: Returns an array containing the command-line arguments passed to the Node.js process.

```js
console.log('Process ID:', process.pid);
console.log('Current directory:', process.cwd());
console.log('Command-line arguments:', process.argv);
```

4. Exit and Signals:

- process.exit([exitCode]): Exits the Node.js process with an optional exit code.
- process.on('exit', callback): Registers a callback to be executed when the Node.js process exits.
- process.on('SIGINT', callback): Handles the interrupt signal (Ctrl+C) and allows graceful shutdown.

```js
process.on('exit', (code) => {
  console.log(`Exiting with code ${code}`);
});

process.on('SIGINT', () => {
  console.log('Received SIGINT signal');
  process.exit(0); // Exit gracefully
});
```

# JS vs C++

Execution Environment:

- JavaScript: It runs within a host environment (e.g., web browser, Node.js runtime). This environment provides APIs (Application Programming Interfaces) that allow JavaScript code to interact with the operating system indirectly. For example, in a browser, JavaScript can use the fetch API to make HTTP requests or interact with the DOM.
- C++: It runs as a standalone executable or as part of a larger system. C++ code can directly use system libraries and APIs to interact with the operating system, file system, network, etc.

Access to OS Resources:

- JavaScript: It has limited direct access to OS resources for security reasons. JavaScript executed in a browser is sandboxed and cannot directly access the file system, system processes, or low-level hardware.
  - C++: It has more direct access to OS resources because the compiled code can call system functions and interact with hardware through system APIs.

# NOTE:

`Yes, that's often a significant reason why C++ programs have more direct access to system libraries and APIs. Many system libraries, especially those related to operating systems and hardware interactions, are written in C or C++. This makes it easier for C++ programs to interact with them directly because they can link to these libraries and call their functions.

Additionally, C and C++ are considered low-level languages compared to languages like JavaScript. They provide features and constructs that are closer to the hardware and operating system, such as pointers, memory management control, and direct access to system resources. This makes C++ well-suited for systems programming and interfacing with low-level system components.

In contrast, languages like JavaScript are often executed in a sandboxed environment (e.g., web browser or Node.js runtime) for security reasons. They typically have restricted access to system resources to prevent malicious actions by web scripts. However, they can still interact with the underlying system indirectly through APIs provided by their runtime environments or through communication with backend services.`

# REPL
REPL (READ, EVAL, PRINT, LOOP) is a computer environment similar to Shell (Unix/Linux) and command prompt. Node comes with the REPL environment when it is installed. System interacts with the user through outputs of commands/expressions used. It is useful in writing and debugging the codes. The work of REPL can be understood from its full form:

Read : It reads the inputs from users and parses it into JavaScript data structure. It is then stored to memory.
Eval : The parsed JavaScript data structure is evaluated for the results.
Print : The result is printed after the evaluation.
Loop : Loops the input command. To come out of NODE REPL, press ctrl+c twice

## Buffer Class
Buffer The Buffer class is an inbuilt globally accessible class that means it can be used without importing any module. The Buffer class is used to deal with binary data. Buffer class objects are used to represent binary data as a sequence of bytes. 
```js
const buffer = new Buffer.alloc(5, "abcde");
```
## Process Object
It is an inbuilt global object that is an instance of EventEmitter used to get information on current process. It can also be accessed using require() explicitly. 

## Console Object
It is an inbuilt global object used to print to stdout and stderr. 

## Global Object
It is a global namespace. Defining a variable within this namespace makes it globally accessible. 

## TextEncoder Object
It is an implementation of the WHATWG Encoding Standard TextEncoder API. All instances of TextEncoder are encoded in UTF-8 only. 

```js
const encoder = new TextEncoder();
const e = encoder.encode("hello world");
console.log(e);
```

## TextDecoder Object

It is an implementation of the WHATWG Encoding Standard TextDecoder API. 
```js
const decoder = new TextDecoder();
const d = decoder.decode(e);
console.log(d)
```
## URL
URL The URL class instance is a global object and is implemented by the following WHATWG URL Standard. The URL constructor creates a new URL object.

## URLSearchParams
URLSearchParams API is used to perform read and write operations on the query of a URL.

```js
const myURL = new URL('https://www.register.com/?name=gfg');

console.log(myURL.searchParams.get('name'));

myURL.searchParams.append('name', 'xyz');

console.log(myURL.href);
```
## WebAssembly
The global object that acts as a namespace for all W3C WebAssembly related functionality. WebAssembly is a low level Assembly-like language that can be run on modern browsers. 

# The following variables might appear to be global but actually exist only within the scope of some modules
- exports: It is used to exports modules using module.exports.

- module: It is a reference to the current module and is not global rather local to each module. It is used to make a particular module available through require() in the application. 
 
- __dirname: The output throws an error which proves that __dirname is not globally defined in node.js. It requires a script to give the desired output as __dirname is only defined in scripts.
  
- __filename: The output throws an error which proves that __filename is not globally defined in node.js. It requires a script to give the desired output as __filename is only defined in scripts.

# Node Modules
In Node.js, Modules are the blocks of encapsulated code that communicate with an external application on the basis of their related functionality. Modules can be a single file or a collection of multiple files/folders. The reason programmers are heavily reliant on modules is because of their reusability as well as the ability to break down a complex piece of code into manageable chunks. 

Modules are of three types:

- Core Modules
- local Modules
- Third-party Modules

Core Modules	Description
- http:	creates an HTTP server in Node.js.
- assert:	set of assertion functions useful for testing.
- fs:	used to handle file system.
- path:	includes methods to deal with file paths.
- process:	provides information and control about the current Node.js process.
- os:	provides information about the operating system.
- querystring:	utility used for parsing and formatting URL query strings.
- url:	module provides utilities for URL resolution and parsing.

# http
To make HTTP requests in Node.js, there is a built-in module HTTP in Node.js to transfer data over the HTTP. To use the HTTP server in the node, we need to require the HTTP module. The HTTP module creates an HTTP server that listens to server ports and gives a response back to the client.
- we can create an HTTP server with the help of http.createServer() method.
- To make requests via the HTTP module http.request() method is used.
  http.request(options[, callback])`

```js
  
const http = require('http');
 
let options = {
    host: 'www.geeksforgeeks.org',
    path: '/courses',
    method: 'GET'
};
 
// Making a get request to
// 'www.geeksforgeeks.org'
http.request(options, (response) => {
 
    // Printing the statusCode
    console.log(`STATUS: ${response.statusCode}`);
}).end();
```


