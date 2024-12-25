# Express.js Server Hang on Unhandled Promise Rejection

This repository demonstrates a common issue in Node.js Express.js applications where unhandled promise rejections within asynchronous request handlers can cause the server to hang.  The error might be logged, but no response is sent to the client, leading to a timeout.

The `bug.js` file contains the problematic code. The `bugSolution.js` demonstrates how to fix this issue using proper error handling and a centralized error handler.

## How to Reproduce

1. Clone this repository.
2. Run `npm install express`
3. Run `node bug.js`
4. Make multiple requests to `http://localhost:3000/`. You'll notice that some requests will hang indefinitely while others will succeed.

## Solution

The solution involves using a centralized error handler (middleware in this case) to catch errors that bubble up from asynchronous operations and send an appropriate response to the client. This prevents the server from hanging and provides a better user experience.