# **Are you a Jedi?**

Category: Web

Author: Siddharth Bhat

Answer / Flag: MAZE{f1r57_ch4ll3ng3_d0n3}

## Problem Statement

*A long time ago in a galaxy far, far away, a secret Jedi Council has devised a challenge to test your Jedi skills. Your mission, should you choose to accept it, is to prove that you are a true Jedi.*

*The website is protected by the Sith Empire, and their supremely good dodging skills. Your goal is to find their secret flag, can you do it?*

*May the Force be with you, young Jedi. May you prove yourself worthy and bring balance to the Force!*

## Relevant files / links

The webpage is zipped using 7z, and is inside the `Chal1` folder. No hosting of the website is required, participants can be simply given the file to download.

## Hint
The Sith love their jumpy tactics and communicate in a very very strange language, but *you* being a Jedi, can use the Force to clear things up and change something in their website to make things much much simpler!

## Solution

The button keeps randomly around the webpage and it is not feasible to click is manually. All the variable and functions are given meaningless names to obfuscate their actual use and purpose.
One brute force solution would be to write a python Selenium script to click on the button 420 times and obtain the flag.
The much simpler method would be to de-obfuscate the function and variable names, and notice that there is a particular variable named `ecqwryionvwniqtywpqiorxmzurcbtrfgdsgfuieewhri` which stores the value of number of clicks left. Since the players have the source code on their local machine, they can simply change that number to 1 or 0. They can also disable the functions which cause the buttons to move randomly/on mouse hover/on mouse click.
Then they can simply click the button once, and the flag gets de obfuscated and displayed

The actual flag is stored in base64 format, and passed through a de obfuscation loop doing some exponentiation.