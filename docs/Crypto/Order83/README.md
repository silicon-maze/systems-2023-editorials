# **Order 83**

Category: Crypto

Author: Kirubakaran M G

Answer / Flag: MAZE{Y0U_4R3_MY_0N1Y_H0P3}

## Problem Statement

The Rebel Alliance intercepts a message from the Galactic Empire titled as Order 83. The Alliance knows that the Galactic Empire usually uses modulo inverse functions to encrypt their messages. They also knew from their spies that the **EMPEROR** had ordered an attack to be **SHIFTED** by **7** days. Using the available information, decrypt the message sent by the Emperor to Darth Vader. 

Alphabet used in the Star Wars universe: 
ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_{}

Intercepted message:
118
178
345
68
382
407
327
289
187
341
45
30
104
201
158
104
78
220
188
158
104
338
244
283
196
180

## Relevant files / links


## Hint

An Emperor's Cipher in which shift occurs by 7.

## Solution

To decipher the message, you must follow these steps: 
1. Take each number in the array and calculate its modulo 83.
2. Find the modulo inverse of each resulting number with respect to 83.
3. Match the new array of numbers with the corresponding letters in the custom alphabet.
4. Apply a Caesar shift of 7 letters to the left with respect to given custom alphabet. 

The solution code is attached here: https://github.com/silicon-maze/Systems-2023/blob/Kiruba-crypto-1/Crypto/Order83/Order83_solution.cpp


