# From Galaxy to Galaxy

Category: Forensics

Author: Dhruva

Answer / Flag: `MAZE{H4ndsh4kes_1n_th3_5t4rs}`

## Problem Statement

In a covert interstellar mission, Luke and Han Solo must exchange classified data over a network. This network might be under the close surveillance of stormtroopers and hence their messages are not in plain text. Can you find the message and decrypt it?

## Relevant files / links

https://drive.google.com/file/d/1UV-3yV_atrKbtkG4DmeRAj1CUhXACiLv/view?usp=sharing contains the network traffic


## Solution

This is basic packet capture analysis. <br>
If you open the .pcapng file on wireshark, you can see the packets being sent between 10.0.0.1 and 10.0.0.2, all of them being Internet Control Message Protocol (ICMP) echo requests (pings), execpt for one packet which uses the TCP protocol.<br>
You can find this packet using different ways but the easiest is to add `tcp.flags.syn==1` in the filters.<br>
This leads you to the packet and then following the TCP stream gives you the base64 encoded version of the flag.