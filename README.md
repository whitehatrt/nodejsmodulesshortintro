
# NodeJs v14.18.0
## Modules Short Introduction

    1. Assert:- provides a set of assertion functions for verifying invariants.
        Ex:- const assert = require('assert');
             assert.deepEqual(/a/gi, new Date());
#  
    2. Buffer:- Buffer class stores raw data similar to an array of integers but corresponds to a raw memory allocation outside the V8 heap. Buffer class is used because pure JavaScript is not compatible with binary data.
        Ex:- // Creates a zero-filled Buffer of length 10.
                const buf1 = Buffer.alloc(10);
# 
    3. child_process:- provides the ability to spawn subprocesses
        Ex:- const { spawn } = require('child_process');
            const ls = spawn('ls', ['-l', '/usr']);
# 
    4. Cluster:-  the user will sometimes want to launch a cluster of Node.js processes to handle the load.
        Ex:- const cluster = require('cluster');
             const http = require('http');
             const numCPUs = require('os').cpus().length;
 
             if (cluster.isMaster) {
             console.log(`Master ${process.pid} is running`);
 
             // Fork workers.
             for (let i = 0; i < numCPUs; i++) {
                 cluster.fork();
             }
 
             cluster.on('exit', (worker, code, signal) => {
                 console.log(`worker ${worker.process.pid} died`);
             });
             } else {
             // Workers can share any TCP connection
             // In this case it is an HTTP server
             http.createServer((req, res) => {
                 res.writeHead(200);
                 res.end('hello world\n');
             }).listen(8000);
 
             console.log(`Worker ${process.pid} started`);
             }
             * Output *
                node server.js
                Master 3596 is running
                Worker 4324 started
                Worker 4520 started
                Worker 6056 started
                Worker 5644 started
# 
    5. Crypto:- provides cryptographic functionality that includes a set of wrappers for OpenSSL's hash, HMAC, cipher, decipher, sign, and verify functions.
        Ex:- const crypto = require('crypto');
             const secret = 'abcdefg';
             const hash = crypto.createHmac('sha256', secret)
                                .update('I love cupcakes')
                                .digest('hex');
             console.log(hash);
             // Prints:
             //   c0fa1bc00531bd78ef38c628449c5102aeabd49b5dc3a2a516ea6ea959d6658e
# 
    6. Filesystem(fs):- enables interacting with the file system.
        Ex:- import { open } from 'fs/promises';
             let filehandle;
             try {
               filehandle = await open('thefile.txt', 'r');
             } finally {
               await filehandle?.close();
             }
# 
    7. Net:- provides an asynchronous network API for creating stream-based TCP or IPC servers.
        Ex:- const net = require('net');
             const blockList = new net.BlockList();
             blockList.addAddress('123.123.123.123');
             blockList.addRange('10.0.0.1', '10.0.0.10');
             blockList.addSubnet('8592:757c:efae:4e45::', 64, 'ipv6');
# 
    8. OS:- provides operating system-related utility methods and properties
        Ex:- const os = require('os');
             os.cpus() //Returns an array of objects containing information about each logical CPU core.
# 
    9. Path:- provides utilities for working with file and directory paths.
        Ex:- const path = require('path');
             path.basename('/foo/bar/baz/asdf/quux.html');
# 
    10. Readline:-  provides an interface for reading data from a Readable stream(Command Line Input)
            Ex:- const readline = require('readline');
                 const rl = readline.createInterface({
                   input: process.stdin,
                   output: process.stdout
                 });
                 
                 rl.question('What do you think of Node.js? ', (answer) => {
                   // TODO: Log the answer in a database
                   console.log(`Thank you for your valuable feedback: ${answer}`);
                 
                   rl.close();
                 });

## Information Source

[NodeJs Docs](https://nodejs.org/dist/latest-v14.x/docs/api/)

  
