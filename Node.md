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