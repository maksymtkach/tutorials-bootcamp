# Intro to Server-side JavaScript

## Contents

- [Creating a Server with Node.js](#creating-a-server-with-nodejs)
  - [Characteristics of Node.js](#characteristics-of-nodejs)
  - [Writing a Simple Web Server](#writing-a-simple-web-server)
  - [Running the Server](#running-the-server)
  - [Express.js Overview](#expressjs-overview)

- [Working with Node.js Modules](#working-with-nodejs-modules)
  - [Understanding Packages and Modules](#understanding-packages-and-modules)
  - [Practical Example](#practical-example)

- [Advanced Node.js Modules](#advanced-nodejs-modules)
  - [Types of Modules](#types-of-modules)
  - [Important Core Modules](#important-core-modules)

- [Overview of NPM](#overview-of-npm)
  - [What is a Package Manager?](#what-is-a-package-manager)
  - [Key Functions of NPM](#key-functions-of-npm)
  - [Understanding the `package.json` File](#understanding-the-packagejson-file)
  - [Local vs. Global Installation](#local-vs-global-installation)

- [Cheatsheet](#cheatsheet)


### **Characteristics of Node.js**

Node.js is a server-side platform built on Google Chrome's JavaScript runtime. It's designed to build scalable network applications. Here are the primary characteristics of Node.js:

- **Single-Threaded but Highly Scalable**: Node.js uses a single-threaded model with event looping. This event mechanism helps the server to respond in a non-blocking way and makes the server highly scalable as opposed to traditional servers which create limited threads to handle requests.
  
- **Non-blocking I/O Operations**: Node.js handles I/O operations asynchronously. Instead of pausing the execution to wait for data, Node.js uses callbacks to signal the completion of a task.
  
- **JavaScript as the Programming Language**: Using JavaScript on both the frontend and backend increases efficiency and reduces the learning curve, enabling developers to understand and build applications faster.

- **Module-based Structure**: Every file in a Node.js application is considered a module that can be reused across different parts of the application. This modular architecture supports better maintainability and scalability.

### **Writing a Simple Web Server with Node.js**

Below is a step-by-step guide to creating a basic web server using Node.js:

#### Import Required Modules
First, you need to import the HTTP module which allows Node.js to transfer data over the HyperText Transfer Protocol (HTTP).

```javascript
const http = require('http');
```

#### Create Server
You use the `http.createServer()` method to create a server instance. This method can take a callback function that is called when an HTTP request is received. The callback function takes two arguments: a request (`req`) and a response (`res`) object.

```javascript
const server = http.createServer((req, res) => {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
});
```

Here, `res.writeHead` is used to send a response header to the request, with a status code of 200 (OK) and content type set to plain text. `res.end` sends the response body, which in this case is "Hello World".

#### Listen on a Port
Finally, you make the server listen on a specific port using the `listen` method. The server is now capable of accepting incoming requests on this port.

```javascript
server.listen(8080, () => {
  console.log('Server running at http://127.0.0.1:8080/');
});
```

### **Running the Server**

To run the server, you would save the above code in a file, for example `server.js`, and then run it using Node.js by executing the command `node server.js` in your terminal. This will start the server, and it will begin listening on port 8080.

Accessing `http://127.0.0.1:8080/` in your web browser would display "Hello World".

### Express ?

The method of creating a web server directly with Node.js's native HTTP module, as described, is fundamental but not outdated. It's a great way to understand how HTTP interactions work at a lower level in Node.js. However, for practical applications, especially those that require more complex routing, middleware support, and additional features, using a framework like Express.js is indeed more common and often recommended.

### Why Express.js is Preferred:

1. **Simpler Syntax and Routing**: Express provides a simplified way of handling server routing, which is the process of determining how an application responds to a client request to a particular endpoint. With Express, you can easily organize your routing and make it more readable.

2. **Middleware Support**: Middleware functions are those that have access to the request object (`req`), the response object (`res`), and the next middleware function in the application’s request-response cycle. These functions can execute any code, make changes to the request and the response objects, end the request-response cycle, and call the next middleware function. Express allows you to use existing middleware or write your own, thereby enhancing the functionality of your applications significantly.

3. **Easier Error Handling**: Express provides a more straightforward way to handle errors through middleware that can catch and manage errors seamlessly.

4. **Community and Ecosystem**: Express has a large community and a robust ecosystem of plugins, which can help you quickly add functionalities to your application.

5. **Template Engine Integration**: Express allows you to seamlessly integrate with various templating engines, making it easier to generate responses based on various templates.

### Example: Creating the Same Server Using Express

Here’s how you can create the same "Hello World" server using Express.js:

```javascript
const express = require('express');
const app = express();
const port = 8080;

app.get('/', (req, res) => {
  res.send('Hello World');
});

app.listen(port, () => {
  console.log(`Server running at http://127.0.0.1:${port}/`);
});
```

### Steps to Run the Server:

- Install Express using npm: `npm install express`
- Save the above code in a file, for example, `app.js`.
- Run the server by executing `node app.js` in your terminal.

As you can see, the code is more streamlined, and it’s easier to extend for more routes, middleware, or error handling. For modern web applications, using frameworks like Express.js usually results in faster development times and more maintainable code, making it a better choice for both beginners and experienced developers alike, especially for more complex applications.

Welcome to a concise tutorial on working with Node.js modules. This guide will walk you through the essential concepts related to Node.js packages, how to import modules into your script, export functions, and access exported properties. By the end of this tutorial, you'll have a solid understanding of these foundational elements of Node.js development.

## Understanding Node.js Packages and Modules

**Node.js Packages**: 
   - A package in Node.js is essentially a directory containing one or more modules, along with a `package.json` file which describes the package details such as its dependencies, version, and main entry script.
   - The `package.json` file serves as a manifest for the package. It specifies metadata about the package such as the name, version, and main script. For example:
     ```json
     {
       "name": "today",
       "version": "1.0.0",
       "main": "lib/today.js"
     }
     ```
   - If no `package.json` is present, Node.js defaults to using `index.js` as the main class or script.

**Importing Modules**:
   - Use the `require` function to import modules. This function loads and caches JavaScript modules provided by Node.js or your application.
   - The `require` function allows importing from a relative path or a node_modules directory. For instance:
     ```javascript
     const today = require('./lib/today');
     ```

**Exporting Functions and Properties**:
   - Node.js modules use the `exports` object to make functions and properties available outside the module file.
   - To export a function or a property, you add it to the `exports` object. For example, to export a function that returns the current day of the week:
     ```javascript
     exports.dayOfWeek = function() {
       return new Date().getDay(); // Returns a number representing the day of the week
     };
     ```

**Accessing Exported Properties**:
   - When you import a module, the `require` function returns an object representing the module. You can access any exported property or function using this object. For example:
     ```javascript
     const today = require('./today');
     console.log('Today is day number:', today.dayOfWeek());
     ```

### Practical Example

Here's a practical example illustrating the entire process:

- **today.js**: This is our module.
  ```javascript
  // File: today.js
  exports.dayOfWeek = function() {
    return new Date().getDay(); // Assuming 1 is Monday
  };
  ```

- **app.js**: This is our main application file.
  ```javascript
  // File: app.js
  const today = require('./today');
  console.log('Today is day number:', today.dayOfWeek()); // Calls the exported function
  ```

To run the application, ensure you have Node.js installed, save the scripts, and run `node app.js` from your command line.

## Advanced Node.JS Modules

After completing this reading, you will be able to describe the three types of Node.js modules. 
You will also be able to explain what several prominent core modules can be used for.

**Libraries** are the same thing as **modules** in regard to Node.js. 
Libraries contain code that has been developed that can be reused throughout an application. 
There are three types of modules: **core**, **local**, and **third-party**.

1. **Core Node.js modules** form a minimal library. 
They contain the minimal functionality needed to develop Node.js applications.

2. **Local modules** are the next type of Node.js module.
Local modules are the modules written by you and the development team as part of creating your Node.js application.

3. **Third-party modules** are available online and have been created by the back-end Node.js community.
These libraries are available to use as stated per their licenses.
Many third-party modules are either in the public domain, which does not require a license, or they are open source.
Open source resources are usually governed by the "copyleft" license, which allows the developer to use and modify the code but also requires the developer to share their work under that same license.

4. The most important of the core modules are **http**, **path**, **fs**, **os**, **util**, **url**, and **querystring**.
Let's briefly discuss each of these and provide code examples.

### HTTP module

The **http module** provides methods to transfer data over HTTP. 
To include the http module in your application, you should **require** it.

Here is sample code that creates an instance of a server using the http module. 
This code makes use of the http.createServer() method to create the server instance.
```javascript
let http = require('http');
http.createServer(function (req, res) {
    res.write('hello from server');//write a response to the client
    res.end();//end of response from server
}).listen(6000);//the server instance listens for http requests on port 6000
```
### FS module

The fs module is used to interact with a file system. 
It does not need to be installed because it is part of the Node.js core and can simply be required. 
The following code sample reads a local file synchronously using the fs module and prints the file contents to the console.
```javascript
const fs = require('fs');
// Synchronously read the file 'sample.txt' and store its contents in 'data'
const data = fs.readFileSync('sample.txt', 'utf8');
// Print the contents of 'sample.txt' to the console
console.log(data);
```
The fs module can also be used for input and output, known as I/O. 
The fs module methods can be used to retrieve information from or write data to an external file.
```javascript
const fs = require('fs');
// Read the contents of the file '/content.md' synchronously and store them in 'data'
const data = fs.readFileSync('/content.md', 'utf8');
// Print the contents of 'content.md' to the console
console.log(data);
```
### OS module

The OS module provides methods to retrieve information from the operating system that the application is running on and interact with it. This is sample code from the OS module that gets the computer's platform and architecture.

```javascript
let os = require('os');
console.log("Computer OS Platform Info : " + os.platform());
console.log("Computer OS Architecture Info: " + os.arch());
```
### PATH module

The path module allows you to retrieve and manipulate directory and file paths.
The following code retrieves the last portion of a given file path and prints that value to the console:
```javascript
const path = require('path');
let result = path.basename('/content/index/home.html');
console.log(result); //outputs home.html to the console
```
### UTIL module

The Node.js util module is intended for internal use for accomplishing such tasks as debugging and deprecating functions. 
Say you want to debug a program to count the number of iterations in a loop. 
You could use **util.format()** method as follows:
```javascript
let util = require('util');
let str = 'The loop has executed %d time(s).';
for (let i = 1; i <= 10; i++) {
    console.log(util.format(str, i)); //outputs 'The loop has executed i time(s)'
}
```
### URL module

The URL module is used to divide up a web address into readable parts. 
Here is a sample code that returns the value of the "firstName" query object from the given URL.

```javascript
const url = require('url');
let webAddress = 'http://localhost:2000/index.html?lastName=Kent&firstName=Clark';
let qry = url.parse(webAddress, true);
let qrydata = qry.query; //returns an object: {lastName: 'Kent', firstName: 'Clark'}
console.log(qrydata.firstName); //outputs Clark
```
### QUERYSTRING module

The querystring module provides methods to parse through the query string of a URL.
For example,
```javascript
let qry = require('querystring');
let qryParams = qry.parse('lastName=Kent&firstName=Clark');
console.log(qryParams.firstName); //returns Clark
```

## Overwiew of the NPM

### What is a Package Manager?

A package manager is a software tool that **automates** the process of **installing**, **upgrading**, **configuring**, and **removing** computer programs for a computer's operating system in a consistent manner. 
It **manages** **modules** and **packages** that contain **code**, **dependencies**, and **libraries** needed by programs to operate effectively.

### Key Functions of NPM

NPM serves two primary functions in the Node.js environment:

1. **Command Line Interface (CLI):**
NPM provides a CLI that allows developers to publish and manage the accessibility of packages.
This interface is used to execute commands such as installing and updating packages, setting up initial new projects, and more.

3. **Online Repository:**
NPM acts as a repository for Node.js packages.
This repository stores numerous packages provided by developers globally and makes them available for you to include in your projects.
It keeps track of all versions of every package published to it, aiding in version control and dependency management.

### Understanding the `package.json` File

The `package.json` file is a core component of managing packages in a Node.js environment. 
It resides in the root directory of any Node.js project or module and contains metadata about the project. Here’s what it typically includes:

- **Name and Version:** These fields are essential as they uniquely identify the package.
- **Dependencies:** Lists all other packages that the project depends on.
- **Scripts:** Defines various commands like start and test scripts.

Example of a basic `package.json`:
```json
{
  "name": "example-project",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.17.1"
  }
}
```

### Local vs. Global Installation

When it comes to installing packages using NPM, you can choose between a local or a global installation:

- **Local Installation:**
This is the default mode. When you install packages locally, they are saved into the `node_modules` directory inside your project's folder and can only be accessed by the project. Use the command:
  ```bash
  npm install <package_name>
  ```

- **Global Installation:**
Packages installed globally are stored in a system-wide location, which can be accessed by any project on your computer. This is useful for CLI tools you wish to run from anywhere. However, it’s important to manage global packages carefully to avoid version conflicts. To install globally:
  ```bash
  npm install -g <package_name>
  ```

### Practical Implications

- **Local installs** are preferable for dependencies that are specific to a project to ensure that the project's environment is consistent and insulated from system-level changes.
- **Global installs** are suitable for tools that need to be run across multiple projects, like npm itself or other CLI tools.

| Term                 | Definition                                                                                                                                                                                                                                                                                                     |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Anonymous Function   | A function that is not named. An anonymous function is often passed into another function as a parameter.                                                                                                                                                                                                       |
| Application Server   | Transforms data into dynamic content and runs the business logic, which is the data storage and transfer rules.                                                                                                                                                                                                |
| Asynchronous         | A process that runs independently of other processes.                                                                                                                                                                                                                                                          |
| Callback Function    | A function passed into another function as a parameter, which is then invoked inside the outer function to complete an action. Instead of blocking on asynchronous I/O operations, callback functions are used to handle results when the operations complete.                                                  |
| Database Server      | A server dedicated to providing database services.                                                                                                                                                                                                                                                             |
| Dependencies         | Code, usually in the form of libraries and packages, that are called from other modules and reused in a program.                                                                                                                                                                                                |
| Event-Driven         | Where the flow of a program is determined by particular events such as user input.                                                                                                                                                                                                                              |
| Express.js           | A highly configurable web framework for building applications on Node.js.                                                                                                                                                                                                                                      |
| Framework            | Generates code that cannot be altered to perform common tasks. Examples include Django, Ruby on Rails, and Express.js.                                                                                                                                                                                          |
| HTTP Server          | A type of software-based server that understands URLs and hypertext transfer protocol.                                                                                                                                                                                                                          |
| Load                 | Refers to the number of concurrent users, the number of transactions, and the amount of data transferred back and forth between the clients and servers.                                                                                                                                                         |
| Module               | Files containing related, encapsulated JavaScript code that serve a specific purpose.                                                                                                                                                                                                                          |
| Multi-Threaded       | Where multiple tasks are executed simultaneously.                                                                                                                                                                                                                                                              |
| Node.js              | A JavaScript runtime environment that runs on Google Chrome’s V8 engine.                                                                                                                                                                                                                                       |
| Non-Blocking         | Failure of a given thread does not cause failure in another, and the execution of a task is not blocked until execution of another task is completed.                                                                                                                                                           |
| Npm                  | Stands for node package manager. It is the default package manager for the Node.js runtime environment.                                                                                                                                                                                                         |
| Package              | A directory with one or more modules bundled together.                                                                                                                                                                                                                                                         |
| Package.json         | Contains metadata information about the project, including dependencies and scripts.                                                                                                                                                                                                                           |
| Payload              | The data transmitted between client and server.                                                                                                                                                                                                                                                                 |
| Runtime Environment  | Behaves similarly to a mini operating system that provides the resources necessary for an application to run. It is the infrastructure that supports the execution of a codebase. It is the hardware and software environment in which an application gets executed. Node.js is an example of a backend runtime environment. |
| Scalability          | The application’s ability to dynamically handle the load as is or shrinks without it affecting the application’s performance.                                                                                                                                                                                   |
| Server.js            | A file that contains the code that handles server creation.                                                                                                                                                                                                                                                    |
| Single-Threaded      | Where only one command is processed at a given point of time.                                                                                                                                                                                                                                                  |
| Web Server           | Ensures client requests are responded to, often using HTTP.                                                                                                                                                                                                                                                    |
| Web Service          | A type of web API that communicates using HTTP requests. It is the web service in the programming interface that sends and receives requests using HTTP among web servers and the client.                                                                                                                      |

## Cheatsheet
**http package** is used for establishing remote connections to a server or to create a server which listens to client.
**createServer** - Takes a requestListener, a function which takes request and response parameters, where request is the handle to the request from the client and response is the handle to be sent to the client.
```javascript
const http = require('http');
const requestListener = function(req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}
const port = 8080;
const server = http.createServer(requestListener);
console.log('server listening on port: '+ port);
server.listen(port);
```

## new Date()	
**new Date()** method returns the current date as an object. You can invoke methods on the date object to format it or change the timezone.
```javascript
module.exports.getDate = function getDate() {
    let aestTime = new Date().toLocaleString("en-US", {timeZone: "Australia/Brisbane"});
    return aestTime;
}
```

## import()	
The import statement is used to import modules that some other module has exported. 
A file that includes reusable code is known as a module.
```javascript
// addTwoNos.mjs
function addTwo(num) {
  return num + 4;
}
export { addTwo };
// app.js
import { addTwo } from './addTwoNos.mjs';
// Prints: 8
console.log(addTwo(4));
```

## require()	
The built-in NodeJS method require() is used to incorporate external modules that are included in different files. 
The require() statement essentially reads and executes a JavaScript file before returning the export object.
```javascript
module.exports = 'Hello Programmers';
let msg = require('./messages.js');
console.log(msg);
```
