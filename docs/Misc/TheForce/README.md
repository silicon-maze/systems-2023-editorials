# **The Force**

Category: Miscellaneous

Author: Suchit

Answer / Flag: `MAZE{HidDeN_GEm}`

## Problem Statement

A disturbance in the Force has revealed two seemingly ordinary images, their true purpose shrouded in secrecy. Your mission is to venture into the depths of these images, guided by subtle whispers, and uncover the concealed flag that will ignite hope for the Rebel cause.The Force flows through all things, even images. Seek the subtlety of shadows and the murmurs of concealed data to uncover the path to the hidden passphrase.


## Relevant files / links

These two images will be given along with the problem statement.

(https://drive.google.com/file/d/1wOQg9Gust_uu32_08Sx3ebeMMsqiDHmX/view?usp=drive_link)
(https://drive.google.com/file/d/1Q9qJj46fvIJl-eFkIhs3OMU6C21otGSg/view?usp=drive_link)

## Hint

It is mentioned in the statement that the data is hidden in the images. So, try using some steganography tools.

## Solution

Since, jpg files are involved, it is reasonable to assume that data is hidden using steghide tool. First we use steghide extract command on the first image (secret_image.jpg). 
This image contains the passphrase to get the data from the second image (secret_image2.jpg) which contains the flag. The passphrase for extracting information from the first
image is an empty string. This can be found by trial and error. The first image contains the following message:<br>
++++++++++[>+>+++>+++++++>++++++++++<<<<-]>>>>++++.+++++++++++++.-------.++++++.---------------------.+++++++.+++++++++.+++.-------------------.+++++++++++++++++++++.------------.---.------.+++++++.++++++.-----------.++++++.
One can easily guess that this is brainfuck programming language. By using a brainfuck interpreter, we can find that the passphrase for the second image is ```hunt_for_the_flag```.
Now, if we use steghide extract command on the second image using the above passphrase, we can obtain the flag. The flag is ```MAZE{HidDeN_GEm}```.

