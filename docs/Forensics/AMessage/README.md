# **A Message**

Category: Forensics

Author: Pratham Kiran K

Answer / Flag: `MAZE{Feel_The_Force}`

## Problem Statement

You are a Jedi apprentice who was sent to deliver a message to Master Yoda on the planet Dagobah. However, the person who made the message knew he couldn't write the message in plain text. So he has hidden it in a file with the hopes of you being able to find the message. Can you?

## Relevant files / links

Link for the .svg file : https://drive.google.com/file/d/1fwtH-hC1_XMM64ZmS3q75GffZ7vx_xlP/view?usp=sharing

## Hint

What's that rectangle in the centre hinting about?

## Solution

* The file is not a common .txt file, rather a .svg file.
* On opening the .svg file in any text editer, we find that all the shapes are defined in plain text, and each have a unique ID
* The numbers within the centre oval are hex converted ID values of elements in the file, which upon inspection reveal are rectangle shapes with the same color as the background color.
* These id values are not random, rather they follow an arithmetic progression.
* Once we know the ID's, we can manually go and change the color of the element in the code, or write a script to change those values for us.
* On changing the color to any other color, emerges text written using combination of rectangle, which is the flag.

## Files Context
* Message.svg is the actual file from which the data has to be decoded.
* id_generator.py is a script to generate all the id values and store it in a ids.txt file
* solution.py is a script that goes through the id values in ids.txt and generates the modified SVG code and saves it in the cracked.svg file.