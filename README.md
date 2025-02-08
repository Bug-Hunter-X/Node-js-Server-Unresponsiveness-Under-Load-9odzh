# Node.js Server Unresponsiveness Under Load

This repository demonstrates a common issue in Node.js applications: unresponsiveness under heavy load.  The server, when faced with a large number of concurrent requests, fails to respond promptly or at all to new incoming requests.  This is due to the synchronous nature of certain operations within the request handling.

## Problem Description

The `server.js` file contains a simple HTTP server that introduces a 5-second delay in processing each request.  While this delay is artificial, it simulates the behavior of a resource-intensive operation such as database queries or file I/O. Under heavy load, the event loop gets blocked, making the server unresponsive. 

## Solution

The `serverSolution.js` file demonstrates a solution using asynchronous operations and the `cluster` module for handling multiple requests concurrently, to mitigate the issue.

## How to reproduce
1. Clone the repository.
2. Run `npm install`.
3. Run `node server.js` and send several requests using tools such as `curl` or a load testing tool like k6, while observing CPU Usage.
4. Run `node serverSolution.js` and repeat step 3 to observe the performance improvements. 