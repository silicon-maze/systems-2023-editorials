# **Galactic Memory**

Category: Forensics

Author: Chinmaya Sharma

Answer / Flag: `MAZE{sp3N7_700_L0nG_0n_7h1s}`

## Problem Statement

Amidst the cosmic labyrinth of hidden pathways, a concealed enigma awaits a daring adventurer. Engage the mystical forces that bind reality, navigating the celestial bases to uncover 64 different secrets veiled within the stars. As whispers of forgotten tales echo through the nebulae, decipher the enigmatic trail to unshroud the ancient wisdom that lies dormant, entwined in the cosmic tapestry. Will you rise as a master of Galactic Memory, revealing the unseen past through your journey across the stars?

## Relevant files / links

[DUMP](https://drive.google.com/file/d/1AkntB09wpBV5UByw8hSdotP6Gr1GJ8th/view?usp=sharing)
[BINARY](https://drive.google.com/file/d/1j1dBiH9FNpU9f0h55BbN8LX-VJOdtTRJ/view?usp=sharing)

## Solution

The binary when examined shows that the program loads data from a file and stores it in a buffer before crashing. Tools like gdb or radare2 can be used to examine the core dump to examine the contents of the stack before the program crashed, which will reveal the flag in a base64 format. The flag can be decoded to get the final answer.
