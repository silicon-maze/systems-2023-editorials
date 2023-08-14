# **Rebel Blocks**

Category: Crypto

Author: Chinmaya Sharma

Answer / Flag: `MAZE{Y0D4_15_4W350M3}`

## Problem Statement

You are a rebel hacker who has infiltrated a secret Imperial base. You have discovered a program that runs on a remote server that takes the name of a file with secrets and returns the metadata of the file, but the metadata is encrypted. This part is easy for you, as you are an expert hacker. Break the encryption and find the flag.

## Relevant files / links

[The Program](https://drive.google.com/file/d/1kofDwejAYXwXyzbmn36nb0_r8b-OHLJn/view?usp=sharing)

## Solution

The program uses `gets` which is vulnerable to buffer overflow. We can use this to overwrite the metadata variable. The metadata is 48 bytes long, and the aes ecb encrypts 16 bytes as a block (since it is a block cipher). Since we can overwrite the metadata variable, 
- we can overwrite the first 15 bytes of the first block of the metadata with a's (or any other known character). 
- we then store the encrypted bytes of the first block
- we then overwrite the first 16 bytes, the last byte being all possible bytes, and then compare the encrypted bytes of the first block with the stored encrypted bytes. When the last byte is the correct byte, the encrypted bytes will match.

Repeat this process to obtain all the bytes of the first block, and then repeat the same for the second block. After the encryption is broken, the text obtained is "Got it,here is a CTF flag MAZE{Y0D4_15_4W350M3}".