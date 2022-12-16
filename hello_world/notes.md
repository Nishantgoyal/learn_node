# Hello World Example

```js
    // Including the http module
    const http = require("http");

    const hostname = "127.0.0.1";
    const port = 3000;

    // creates a new HTTP Server
    const server = http.createServer((req, res) => {
        // Indicate a successful response
        res.statusCode = 200;
        res.setHeader("Content-Type", "text/plain");
        res.end("Hello World\n");
    });

    // Server starts listening
    server.listen(port, hostname, () => {
        console.log(`Server running at http://${hostname}:${port}/`);
    });
```

------
## HTTP Module

The node.js HTTP API is very low level. It deals with stream handling and message parsing only.  
It parses a message into headers and body but it does not parse the actual headers or the body.  
To use the HTTP Server and Client one must `require('node:http')`.  

HTTP Module [Documentation](https://nodejs.org/api/http.html)

------
## HTTP Server

The `createServer()` method of `http` creates a new HTTP Server and returns it.  
The server is set to listen on the specified port and host name.  
```js
    server.listen(port, hostname, callback_function)
```
When the server is ready, the `callback function` is called, in this case informing us that the server is running.  

Whenever a new request is received, the `request event` is called, providing two objects
- a request -- an `http.IncomingMessage` object  
    
    It provides the request details, like request headers and request data
- a response -- an `http.ServerResponse` object 
 
    It is used to return data to the caller