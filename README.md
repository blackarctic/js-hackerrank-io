# JS HackerRank I/O Reference

A reference for handling I/O to JavaScript applications on HackerRank.

## Template

```js
"use strict";

let fs = require("fs");

const LOCAL = false;   // set if testing on a local machine
const DEBUG = false;   // set if debug messages should be displayed
const LOCAL_INPUT = "input.txt";     // set local input file path 
const LOCAL_OUTPUT = "output.txt";   // set local output file path 

/*** output functions ***/

function debug (s) {
    if (DEBUG) { console.log(s); }
}
function write (s) {
    if (LOCAL) { wstream.write(s+"\n"); }
    else { console.log(s); }
}

/*** io handling ***/

var input_stdin = "";
var input_stdin_array = "";
var input_currentline = 0;
var rstream;
var wstream;
function readLine () {
    return input_stdin_array[input_currentline++];
}
function handleDataIn (data) {
    input_stdin += data;
}
function handleDataEnd () {
    input_stdin_array = input_stdin.split("\n");
    main();
}
if (LOCAL) {
    wstream = fs.createWriteStream(LOCAL_OUTPUT);
    wstream.on("finish", () => { debug("done"); });
    rstream = fs.createReadStream(LOCAL_INPUT);
    rstream.on("data", handleDataIn);
    rstream.on("end", handleDataEnd);
}
else {
    process.stdin.resume();
    process.stdin.setEncoding("ascii");
    process.stdin.on("data", handleDataIn);
    process.stdin.on("end", handleDataEnd);
}

/////////////////////////////////////////////
///////// YOUR CODE BELOW THIS LINE /////////
/////////////////////////////////////////////




function main() {

    // your code here
    
    if (LOCAL) { wstream.end(); }
}
```


## Config

Be sure to set the config variables at the top to your preference:

* `LOCAL` should be set if testing on a local machine (default: `false`).

* `DEBUG` should be set if debug messages should be displayed (default: `false`).

* `LOCAL_INPUT` should be set to your local input file path (default: `input.txt`).

* `LOCAL_OUTPUT` should be set to your local output file path (default: `output.txt`).

`DEBUG` and `LOCAL` should both be set to `false` when submitting code on HackerRank. 

## Usage

Use `debug()` for selective output when debugging

```js
debug(`foo(): called with a = ${a} and b = ${b}`);
```

Use `write()` for normal output

```js
write(`YES`);
```

Use `readLine()` to read in a line from the input source. (This does not inlcude the newline character.)

```js
let line = readLine();
```

## Info

No affiliation with or to HackerRank