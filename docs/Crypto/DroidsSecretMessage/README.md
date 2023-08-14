# **Droid's Secret Message**

Category: cryptography

Author:ujjwal

Answer / Flag: `MAZE{MAY_THE_FORCE_BE_WITH_YOU}`

## Problem Statement

A droid carrying critical information crash-landed on an unknown planet. The Resistance needs your help to recover the encrypted message it was carrying. Your mission is to decrypt the message and find the hidden flag. The encryption method involves a technique inspired by a French Man whose name is JEDI. May the Force guide you!

Encrypted Message: VECM{VEB_BQI_IWAGH_JN_ALBQ_CRC}

## Hint

The method used to safeguard this message is steeped in history and intrigue. Think about the art of shifting and mixing letters, a technique known to cryptographers for centuries, or maybe you can take help from that French man whose name is JEDI.

## Solution

To decrypt the message, we need to apply a modified version of the Vigenère cipher using a Star Wars-related keyword.

Star Wars-related keyword that will act as the decryption key. For this question, is the keyword "JEDI"

Convert the keyword to numeric values based on their positions in the alphabet (A=0, B=1, C=2, etc.):
J → 9
E → 4
D → 3
I → 8

Apply the Vigenère cipher decryption using the numeric values of the keyword. Subtract each corresponding keyword value from the numeric value of the corresponding ciphertext letter, wrapping around if necessary. 

For example, to decrypt the first letter 'D':
D (3) - 9 (J) = -6 (wrap around) = 20 (T)

Decrypt each letter of the ciphertext using the corresponding keyword value and repeat the process for the entire message.

Applying the Vigenère cipher decryption in the encrypted text using the keyword "JEDI":

The resulting decrypted message is "MAZE{MAY_THE_FORCE_BE_WITH_YOU}."


