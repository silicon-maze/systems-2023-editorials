# The Secret Code Of The Star Wars Galaxy

Category: Cryptography

Author: Dhruva

Answer / Flag: `MAZE{L1ghts4b3r}`

## Problem Statement

In a distant galaxy, during the age of the Jedi Order, a mysterious artifact has been unearthed on the ancient planet of Coruscant. The artifact holds secrets of great importance, but it is protected by a powerful encryption.

Upon inspecting the artifact, the Rebel Alliance discovers an encrypted message.

"4d415a4574b8698e6874733456924c48"


This was found along with the encrypted message:<br>

"Faint echoes of the stars, a riddle to explore<br>
Enigmatic paths they weave, secrets to adore.<br>
In realms of ciphered tales, mysteries galore,<br>
Silent whispers guide the brave, forevermore.<br>
The cryptic dance begins, a ballet of codes,<br>
Enveloping the message, the truth it holds.<br>
Luminous rounds of transformation, the tale unfolds."<br>

We also found this and suspect that it might be somehow connected with the encryption :

```cpp
unsigned int get_hash(string s, const int n long long key) 
{
    long long m = 1e9 + 7;
    long long hash = 0;
    long long p_pow = 1;
    for(int i = 0; i < n; i++) {
        hash = (hash + (s[i] - 'a' + 1) * p_pow) % m;
        p_pow = (p_pow * key) % m;
    }
    return hash;
}

//[31,17,37,13,29]
```
Your mission is to decipher the hidden message and unlock the knowledge held within the artifact. Embrace the ways of the Jedi and use your intuition to reveal the secrets hidden behind this galactic encryption.

May the Force guide you on this quest, and may the knowledge within the artifact aid the Rebel Alliance in their fight for freedom and justice across the galaxy!
</li>

## Solution
<ul>
<li>The first letter of each line of the poem when put together spells out "FEISTEL"</li>
<br>

[Here is material on the Feistel structure](https://en.wikipedia.org/wiki/Feistel_cipher)

<li>To decrypt the hexadecimal string you apply the rounds in the reverse order, that is, the keys are just used in reversed order
</li>
<li>All the functions required to encrypt and decrypt text are given in the <b>solution.cpp</b>
file
</li>
</ul>