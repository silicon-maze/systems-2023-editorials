# **Star Wars Key Maze**

Category: `Web`

Author: Vignaraj

Answer / Flag: MAZE{ReCur$e_ThE_P@th_T0_P0w3R}

## Problem Statement

A long time ago, in a galaxy far, far away, a secret Jedi order known as "The Keepers of the Force" established a hidden repository of ancient knowledge. The repository holds the keys to unlocking the ultimate power of the Force. As a young Jedi initiate, you are tasked with embarking on a perilous quest to navigate the recursive pathways of the Jedi Code. Your journey begins with a mysterious initial key, whispered by the Force itself. Each key you uncover will reveal the path to the next, but beware, for the dark side of the Force is cunning. With every step you take, the challenges grow stronger, testing your wisdom and intuition. Your ultimate goal is to reach the heart of the repository, where the final flag awaits, empowering you with the knowledge of the Jedi Masters. May the Force be with you on this epic adventure, young Jedi!

## Relevant files / links

`website needs to be deployed`

## Hint

"Amidst the galactic turmoil, a hidden path awaits. Embrace the power of the POST, traverse the recursive depths, and unlock the Force's secrets in your quest for Jedi ascendance."


## Solution

Using POST requests, they must navigate through a series of keys provided by the website. Each POST request will yield the next key in the sequence. The challenge continues until the last page is reached, where no form or next key is presented. At this point, the key displayed is the final flag. Participants can employ programming languages like Python and libraries like requests to automate the process. By iterating through POST requests and checking for the absence of a next key, they will eventually uncover the hidden flag.