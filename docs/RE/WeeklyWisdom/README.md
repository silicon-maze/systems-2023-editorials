# **Weekly Wisdom**

Category: RE/PWN

Author: Kirubakaran M G

Answer / Flag: MAZE{F33L_TH3_F0RC3}

## Problem Statement

Luke Skywalker visits Yoda on the planet Dagobah. Dagobah is a remote and swampy planet in the Star Wars universe and serves as the hiding place for Yoda during his 
self-imposed exile after the fall of the Jedi Order. It is in the dense jungles of Dagobah that Luke seeks out Yoda for training.Each week, Yoda travels to Luke's location 
to provide him with advice, drawing upon his extensive knowledge and experience in the ways of the Force. 

Out of all the wisdom imparted by Yoda, which advice held the utmost value?

## Relevant files / links
(https://drive.google.com/file/d/14ZeaOflb1nDGQI2UTjxCPKwneWNlxwAO/view?usp=sharing)
## Hint

A week consists of SEVEN days. 

## Solution

Run the given binary file in a disassembler. The main function calls a function called check(), which accepts a int and a string as parameters.  

"3!U3}6M_9-3Y3AF6aL90Z034_X7ER01T)4{C78H01F3(5" - This string is passed and size of the input string is passed as integer. Every 7th letter of the string is concatenated to a empty string 1 by 1 until the new string reaches the size of the input string. . This will return the string "MAZE{F33L_TH3_F0RC3}".Finally the received input is compared with this string and corresponding output is given. 
