# **The Rebel's Hidden Treat: A Star Wars-inspired Confectionery Quest**

Category: Web 

Author: Shubham Rasal

Answer / Flag: `MAZE{slkdjflsktgr5egjf}`

## Problem Statement

A long time ago in a galaxy far, far away, a group of rebel spies intercepted a crucial message from the evil Empire. However, the message was encrypted and hidden  on a mysterious server. It is your mission, as a brave Jedi knight, to retrieve  and decipher the hidden message.


## Requirements

Node.js

The files present in this directory are:
package.json
server.js
package-lock.json

The files server.js , package.json and package-lock.json are required to run the server.
These have to uploaded to the server and then the server has to be started.

## Setup

1. Install Node.js
2. Run `npm install` to install all the dependencies.
3. Run `node server.js` to start the server.


## Hint

Do you know about cookies?

## Solution

This is a simple cookie based challege.

If you observe the GET requests sent by the browser or Postman client , you will notice that the server returns a cookie called `ctf`.

This cookie is set to false by default by the server. You need to set it to true to get the flag.
This flag is a jwt token which is base64 encoded. You can decode it using any online decoder.
After decoding you will find a field called `flag` which contains the flag.
