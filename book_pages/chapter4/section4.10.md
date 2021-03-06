## Section 4.10: Cloning a file using streams

This program illustrates how one can `copy a file` using readable and writable streams 
using the `createReadStream()` , and `createWriteStream()` functions provided by the 
file system module.

```js
//Require the file System module
let fs = require('fs');
/*
Create readable stream to file in current directory (__dirname) named 'node.txt'
Use utf8 encoding
Read the data in 16-kilobyte chunks
*/
let readable = fs.createReadStream(
  __dirname + '/text.txt', 
  { 
    encoding: 'utf8', 
    highWaterMark: 16 * 1024 
  }
);

// create writable stream
let writable = fs.createWriteStream(
  __dirname + '/nodeCopy.txt'
);

// Write each chunk of data to the writable stream
readable.on('data', function(chunk) {
  writable.write(chunk);
});
```