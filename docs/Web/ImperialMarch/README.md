# **Imperial March**

Category: Web 

Author: Aditya Harish

Answer / Flag: `MAZE{d4rth___v4d3r}`

## Problem Statement

The Galactic Empire has captured the Rebel Alliance's secret data containing vital information about the Death Star's vulnerability. Your mission, as a skilled hacker, is to infiltrate their system and retrieve the data. The data is stored in a website that only displays the data to the members of the Rebel Alliance via password protection. Knowing that their passwords wouldn't be stored in plain text, the Rebels did not put much thought into their password and chose a relatively weak one. 
Can you retrieve the data?

## Setup
1. Install Node.js
2. Run `npm install` to install all the dependencies.
3. Run `node server.js` to start the server.

## Solution

On inspecting the source code of the website, the following snippet is seen: `users = [{ username: "admin", password: "bf10b11d540b65020c4440ab894a6d04" },];`. As we know the password used is not strong(from the question description), we can try cracking the hash. The password is hashed using `md5`, and the hash can be cracked using various tools (Eg : https://crackstation.net/). Once the hash is cracked, the password `passhello` is obtained and can be entered in the login page to get the flag.  
