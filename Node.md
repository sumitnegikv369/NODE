## Node.js

- Node.js is an open-source, cross-platform JavaScript runtime environment.
- It allows developers to run JavaScript code outside a web browser, making it versatile for various applications.

## JavaScript Engine

A JavaScript engine is a program responsible for converting JavaScript code into machine code, enabling computers to execute specific tasks defined in JavaScript. One prominent JavaScript engine is V8, developed by Google and open-sourced for wider use. Node.js leverages the V8 engine, which is written in C++ and excels at handling lower-level operations efficiently and by embedding V8 into your own C++ program we have all functionaly in JavaScript.

## JavaScript Runtime Environment

A JavaScript runtime environment encompasses all the necessary components to use and run JavaScript programs effectively. These components include:

- **JS Engine**: Manages memory and the call stack, like V8 in the case of Node.js.
- **Web/Browser APIs**: Provides interfaces for interacting with web functionalities such as the Document Object Model (DOM), storage, and timers.
- **Event Loop**: Facilitates asynchronous operations through microtask queues and callback/task queues, crucial for non-blocking I/O operations in Node.js.
- **Node.js**: In Node.js, the runtime environment includes APIs for interacting with the file system, networking, and other system resources.

## Applications of Node.js

Node.js is versatile and empowers developers to build a wide range of applications, including:

- Traditional websites with dynamic content and server-side logic.
- Backend services like APIs for handling data exchange between clients and servers.
- Real-time applications such as chat apps or collaborative tools leveraging WebSockets for instant communication.
- Streaming services for media delivery and processing.
- Command-Line Interface (CLI) tools for automation and scripting tasks.
- Multiplayer games with real-time interactions and data synchronization.

## Node.js Components

Node.js relies on various components, with dependencies like the V8 engine playing a crucial role in its functioning. These components work together seamlessly to provide a robust environment for developing JavaScript-based applications,C++ features,libuv,etc.

## Node Modules

a module is a piece of reusable JavaScript code. It could be a .js file or a directory containing .js files. You can export the content of these files and use them in other files.

## CommonJS

It is a module system for JavaScript which define standard for structuring or organizing js code into reusable module.CommonJS is mainly used in server-side JS apps with Node, as browsers don't support the use of CommonJS.To achieve this we have require function to import the module and module.exports to export values from a modules.

## Module Wrapper

Every module in node js gets wrapped in a IIFE before loaded which provide scope for the modules code and also inject some variables and function to modules scope

(function(exports, require, module, **filename, **dirname) {
// Module code goes here
});

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
const http = require("http");

const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "text/plain" });
  res.end("Hello from your Node.js server!");
});

server.listen(3000, () => {
  console.log("Server listening on port 3000");
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

In Express.js, we can set status codes using `response.status(code)` and send corresponding messages. For example:

```javascript
response.status(200).send("OK");
response.status(404).send("Not Found");
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

In Nodejs we have no window object because we have no browser functionalty but we have global objects and we can access in anywhere in our application and there multiple global objects in Nodejs

1. dirname and \_\_filename:

- \_\_dirname: Represents the directory name of the current module. It gives you the absolute path of the directory containing the current module file.
- \_\_filename: Represents the filename of the current module. It gives you the absolute path of the current module file.

```js
console.log(__dirname); // Outputs the directory path of the current module
console.log(__filename); // Outputs the file path of the current module
```

2. require:

- require is used in Node.js to include modules (files or packages) in your application.
- You can require your own modules by specifying the file path (./path/to/module) or use npm packages by specifying the package name.

```js
const fs = require("fs"); // Require the built-in 'fs' module
const myModule = require("./myModule"); // Require your own module
```

3. console:

- The console object in Node.js is used for logging messages to the console, debugging, and monitoring the application.
- Common methods include console.log(), console.error(), console.warn(), etc.

```js
console.log("Hello, world!"); // Log a message to the console
console.error("Error message"); // Log an error message
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
process.stdout.write("Enter your name: ");
process.stdin.on("data", (data) => {
  console.log(`Hello, ${data.toString().trim()}!`);
  process.exit();
});
```

3. Process Information:

- process.pid: Returns the process ID of the current Node.js process.
- process.cwd(): Returns the current working directory of the Node.js process.
- process.argv: Returns an array containing the command-line arguments passed to the Node.js process.

```js
console.log("Process ID:", process.pid);
console.log("Current directory:", process.cwd());
console.log("Command-line arguments:", process.argv);
```

4. Exit and Signals:

- process.exit([exitCode]): Exits the Node.js process with an optional exit code.
- process.on('exit', callback): Registers a callback to be executed when the Node.js process exits.
- process.on('SIGINT', callback): Handles the interrupt signal (Ctrl+C) and allows graceful shutdown.

```js
process.on("exit", (code) => {
  console.log(`Exiting with code ${code}`);
});

process.on("SIGINT", () => {
  console.log("Received SIGINT signal");
  process.exit(0); // Exit gracefully
});
```

## Streams and Buffers

Streams is a sequence of data that is being moved from one computer to another or within the same computer.Streams enable us to read/write data continously,basically used to handle large amount of data without loading entire dataset into memory which prevents unnecessary data downloads and memory usage.
Now Buffer is the temporary small storage area in runtime that nodejs maintain to process stream of data.Now how Nodejs works in between it only decide the right time to send data for processing,if data if already processed or too little data to process it puts arriving data to buffer

## Asynchronous JavaScript

As JS is synchronous,blocking and single threaded language problem with these behaviour is it not run the further line of codes until former is completed.
So to achieve Asynchronous behaviour Javascript is not enough we need other pieces of code outside the JavaScript which help us to write asynchronous code,for frontend web browser comes into play for backend Nodejs comes into play.

## Node.js Architecture

Node.js architecture refers to the functionalities and components that determine how code execution occurs within Node.js. Node.js is madeup of V8 engine,libraries like Libuv,etc and other C,C++ featrures. It includes following key components:

1. Event Loop
2. Libuv
3. Event Queue
4. Thread Pool
5. Event-Driven

## Event Loop

As we know that Node.js uses “Single Threaded Event Loop” architecture to handle concurrent client request.The event loop is a core component of libuv and is responsible for managing asynchronous operations in Node.js,as the process start execution Event loop offloads all CPU intensive tasks to the thread pools

## Libuv

It is a crossplatform library written in C lang.It handles the asynchronous non blocking operations with the help of event loop,thread pools,etc which allows nodejs to perform I/O operations without blocking the main thread.It has some queues like timer queue,i/o queue,check queue,clode queue but mictoask queue is not part of libuv.

## Thread Pool

As Node.js is Single threaded which has its main thread to execute the tasks as asynchronous functions, When you call an asynchronous function, which is CPU intensive task not handled by OS then mainthread offloads the task to the thread pool, allowing it to execute concurrently with other operations. This prevents blocking of the main event loop and ensures that your application remains responsive.Libuvs thread pool has 4 threads but it can be increased upo 128.It is used to perform the CPU intensive task like Crypto,etc

## Event Queue

It is a data structure that holds events or tasks to be processed by the event loop. When asynchronous operations such as I/O tasks or timers are completed or when certain events occur, callbacks associated with those operations are added to the event queue.the event queue in Node.js is where callbacks for completed asynchronous operations are queued up for processing by the event loop, enabling non-blocking I/O and asynchronous programming paradigms.
