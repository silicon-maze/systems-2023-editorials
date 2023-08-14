# **Dark Side's Codebreaker**

Category: Pwn

Author: Siddharth Bhat

Difficulty: Easy

Answer / Flag: MAZE{s00p3R_W3Ap0n_uNd3r_DeveL0pM3n7!}

## Problem Statement

*In a galaxy far, far away, a group of droids has stumbled upon a hidden Imperial transmission. Rumor has it that this transmission contains crucial information about the Empire's plan to build a powerful new superweapon. However, the transmission occurs with a peculiar token system that only those who understand the Force can decipher.*

## Relevant files/links

The binary fiile test2 can be shared with everyone. Drive link [here](https://drive.google.com/drive/folders/1D02yfikU4qbNDMSrU8bCvpTWlaqYrQ4Z?usp=sharing)


## Hint
*"After peering through several books in the great library, the masters say that there are certain **limits** to the **size** of the tokens, and that they can be manipulated!"*


## Solution

The challenge is a simple integer overflow. One can reverse engineer the binary and realise that there is a condition checking if the total cost is less than 420xinputTokens. On supplying a sufficiently large number, it it will exceed the limit of `INT_MAX` and cause an integer overflow, which makes the number negative!

The remaining tokens will be tokens - TotalCost but since TotalCost is now negative due to the integer overflow, the remaining number of tokens will be greater than initialised, leading to the secret function being called.
