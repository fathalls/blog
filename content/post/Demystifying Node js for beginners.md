---
date: 2019-07-12
linktitle: Demystifying Node.js for beginners
icon: code-alt
tags : [
    "nodejs",
]
title: Demystifying Node.js for beginners
summary: Node JS and its ecosystem.
---

## tl;dr

This article gives an overview of how Node.js works under the hood along with some pointers to get started with building your first Node.js application.

### JavaScript - Client side & Server side

JavaScript language was originally released in 1997 by Netscape. Its initial goal was to be  a Browser side programming language.

The Browser loads the script,  compiles it on the fly to binary code and executes it.

The need to have consistent codebase across client and server side was growing, therefore a runtime similar to the one running in Browsers was required for servers.

In addition to being a compiler and an optimiser, this runtime has to manage the dependencies between modules and to handle the events received from the client side and the callbacks.

### Node.js

Node.js is a  server side JavaScript runtime. It allows us to run JavaScript on the server-side, by providing dependency management, compiling and event handling capabilities.

It is also famous for being fast and performant compared to similar runtimes.

Below some if its main features:

- **Compiler**: The compiler is built on top of V8 engine. It compiles and executes JavaScript code, it handles the call stack and it manages the memory allocation using  the Garbage Collector.

- **Single Threaded**: It is single threaded, unlike other server side runtimes (e.g. Vertx). Node.js maintains a queue of requests from the client side, processes one request at a time and sends back the response. This makes it performant because the cost of spinning new threads for new incoming requests can be expensive, This is because a large block of memory has to be allocated and initialised for the thread stack, it needs to be registered  in the runtime, which makes it CPU intensive.

- **Non-blocking**: It offers the possibility to have non-blocking code. All I/O operations in Node.js have async versions with callbacks. This is useful in the context of single threaded event loop; we don't want to block the next request to be processed by having blocking code.

- **Dependency Management**: It handles external and internal module dependency. We use NPM (Node Package Manager) to install external modules - or libraries - and the keyword Require (Javascript ES5 or earlier) or Import (JavaScript ES6) to use them in the code. We can also export classes or functions within the same project and use it as an internal dependency in another part of the code. It is always a good practice to separate concerns by creating internal modules.

### Building a Node.js application

Now that we have covered the main features offered by Node.js, we are ready to start building our Node.js server side application. The internet is filled with simple tutorials to build such applications!

Here is a list of the most used modules to build a MERN stack application, MERN stands for MongoDB-Express-React-Node.

- [webpack](https://webpack.js.org/): helps with building and packaging the code into a bundle file, which is compatible and readable by the browser.
- [babel](https://babeljs.io/): transpiles JavaScript ES6 and later versions to JavaScript ES5. Since Browsers are slow to support newer versions of JavaScript, this is a good way to code in JS ES6 without having to worry about browser compatibility.
- [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch): provides an interface to make HTTP requests.
- [express](https://expressjs.com/): is a web framework for Node.js.
- [mongoose](http://mongoosejs.com/): is a mongodb object modelling for node.js.
- [react](https://reactjs.org/): is the React library to build user interfaces.
- [mocha](https://mochajs.org/): is the JavaScript testing framework.

Now that you had a sneak-peak of Node.js main functionalities, let's dive into some programming. Here is official [getting started guide](https://nodejs.org/en/docs/guides/getting-started-guide/) that I find really helpful for newbies.