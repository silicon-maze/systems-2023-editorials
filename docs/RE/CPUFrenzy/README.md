# **CPU Frenzy**

Category: RE/PWN

Author: Srinivasa R

Answer / Flag: `MAZE{g0odP4d4WaN}`

## Problem Statement

Toby wants to play Star Wars on his NES, which is an old gaming device from a long time ago in a galaxy far, far away. He has a special NES that requires a secret code to activate. Toby has forgotten his secret code! Toby knows that the 12-symbol code is hidden somewhere in the memory of the NES, but he doesn’t know where exactly. But he knows that he can find the location of the code by adding the number in the Y slot to the location stored at the first spot in the memory (the location is stored in reverse order, which is called Little Endian).

He attaches a device that always shows 12 symbols from the memory starting from the spot marked E000.

But while modifying the NES to attach the device, he somehow damaged the processor, which caused the wires connecting the A and Y slots to be switched (maybe he accidentally crossed them with his lightsaber) without changing anything else. Fortunately, Toby is in possession of a <a href="https://www.princeton.edu/~mae412/HANDOUTS/Datasheets/6502.pdf">document</a> containing all the magical details needed to figure out how to work around this.

Can you help Toby find his secret code?

## Relevant files / links

The <a href="https://www.princeton.edu/~mae412/HANDOUTS/Datasheets/6502.pdf">Synertek SY6502 datasheet</a>.

`cpu_def` is the binary to be uploaded as it emulates the defective CPU.

`cpu` can also be uploaded although it doesn't contain the flag. Following the correct procedure on this (transferring bytes to the right addresses) will display `wouldBeHere` and is more straightforward.

## Hint

Hint: Toby wonders what is special about the Y register and where it is used when compared to the A register (accumulator).

## Solution

Note: There are many possible ways to achieve the goal. The following shows one possible way which doesn't take a lot of complicated instructions.

Looking at the question, the address to the password is Y + the address stored at $0000. This reminds us of indirect indexed addressing mode (explained in detail in the datasheet).

The opcodes for every instruction can be found on the datasheet.

However, we know that the connections to the accumulator (A) and the Y register is switched. So, using it directly will fail since the offset will be taken from A instead of Y.

So, first we need to transfer the value stored in Y to A. Usually this would be done by the `TYA` instruction (Opcode: `0x98`) but in our case the registers are switched, so we use the `TAY` instruction instead (Opcode: `0xA8`).

Now we can use the instruction `LDA $(00),Y`.

Usually, this instruction would go to \$0000 (it's written as \$(00) in the instruction as we can only write addresses in the first page here, i.e; \$0000 to \$00FF which can be represented by just the lower byte) and read the byte (say `lo`), go to $0001 and read the byte (say `hi`). Then, it would compute `hi * 256 + lo + Y` as the address (let's call it `pass_addr`). Then, it would go to \$(`pass_addr`), read the byte and store it in A.

In our defective CPU, everything would be almost the same except `pass_addr` would be `hi * 256 + lo + A` and the final byte read would be stored in Y.

Now we can go ahead and use `STA $E000`.

Usually, this would write the value stored in A to address $E000 (where we start printing), but in our case it will write the value stored in Y which happens to be where the read value previously was also stored!

Now, to move to the next character, we need to increment the value we index by. In case out CPU wasn't defective, this would be Y as we are indexing by Y but we are actually indexing by A due to the defect. So, we need to increment A. But again as Y and A are switched, we need to use `INY` to increment A!

Now we just repeat the previous three instructions, `LDA $(00),Y` and `STA $E00x` (keep in mind to use \$E001, \$E002, .... in every subsequent repetition until \$E00B) and `INY`. 

Now, to write it in hex form, we can just look up the opcodes in the datasheet. Remember the system is Little Endian, so while writing multi byte values, write the lower byte in the first followed by the higher byte.

`TAY` = `A8` <br>
`LDA $(00),Y` = `B100` <br>
`STA $E000` = `8D00E0` <br>
`STA $E001` = `8D01E0` <br>
`STA $E002` = `8D02E0` <br>
...

The code which moves the entire flag to the printed region ($E000 to $E00B) is:
`A8B1008D00E0C8B1008D01E0C8B1008D02E0C8B1008D03E0C8B1008D04E0C8B1008D05E0C8B1008D06E0C8B1008D07E0C8B1008D08E0C8B1008D09E0C8B1008D0AE0C8B1008D0BE0`
