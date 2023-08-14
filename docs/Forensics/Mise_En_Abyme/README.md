# **Mise_En_Abyme**

Category: Forensics

Author: Bharadwaja MeherRushi Chittapragada

Answer / Flag: `MAZE{P14a5e13n20tI9n20t15oA1b2y19s19}`

## Problem Statement

In a galaxy far, far away, a tale unfolds,<br>
Where Star Wars characters, their destinies behold.<br>
Amidst the stars and the Force's profound might,<br>
A hero embarked on a quest, seeking secrets of light.

Obi-Wan Kenobi, noble and wise,<br>
Ventured into the unknown, his purpose disguised.<br>
Through treacherous galaxies, he journeyed long,<br>
Seeking a secret that was concealed, mysterious and strong.

Upon an ancient planet, covered in mystery's haze,<br>
He stumbled upon a picture, capturing his gaze.<br>
Within that frame, a world of secrets was concealed,<br>
A picture within a picture, a truth unrevealed.

He gazed upon the image, its depths unfurled,<br>
A series of pictures, unfathomably twirled.<br>
Each layer peeled back, revealing a new sight,<br>
An enigmatic tapestry, endless in its infinite flight.

Worlds within worlds, a cosmic puzzle unwound,<br>
Through nebulae and star clusters, he was bound.<br>
Each picture held a message, hidden with care,<br>
A clue to unlock the secret, he must dare.

In a sea of constellations, he focused his sight,<br>
Unraveling the layers, like an ardent Jedi knight.<br>
Each image spoke volumes, in symbols and signs,<br>
Whispering secrets of the Force, that danced between lines.


The final picture emerged, revealing an eye,<br>
A single gaze, piercing the fabric of the sky.<br>
Obi-Wan knew he must act, decipher the clue,<br>
For within that hidden message, the fate of many grew.


In realms of ancient lore and cosmic might,<br>
Obi-Wan Kenobi, valiant in his Jedi light,<br>
Yet technology eluded his skillful hands,<br>
A puzzle unsolved, beyond his command.

With humble gratitude, he turned to you,<br>
Seeking guidance in this digital sea so true.<br>
Forensics knowledge you possessed, a tool so rare,<br>
To aid the noble Jedi in his secret-laden affair.


## Relevant files / links

Link to image : https://drive.google.com/file/d/1alFfKbcs_sDunVsxl0KJQtpbJJWUOyXh/view?usp=sharing

The above `drive` link contains an `image: mise_en_abyme.jpg` and the link has view access to anyone with the link

## Hint

> Within that frame, a world of secrets was concealed,
A picture within a picture, a truth unrevealed.

> The final picture emerged, revealing an eye,
A single gaze, piercing the fabric of the sky.


## Solution

The initial approach would after downloading the image would be to look at it's properties. They are expected to try basic commands like `file`, `strings`, `exiftool`, `identify`, `steghide` and `binwalk`. By going through standard steganography appraoches.  

- Step 1: Either by using binwalk or through identifing the file properties, they will be able to identify that there is another image embeded within this image.

```
$ unzip mise_en_abyme.jpg
```
The output will be as follows:
![Step_1_unzip](solution_images/step1_unzip.png)

or

```
$ binwalk -e mise_en_abyme.jpg
```
The output will be as follows:
![Step_1_binwalk_output](solution_images/Step1_binwalk.png)

The result of this step will either 

- Step 2: There is `mise_en_abyme_1_.jpg` file will be found. The `step 1` can be repeated until (there are 3 levels and the base case is reached) `mise_en_abyme_base.jpg` 

- Step 3: After reaching the base image, you cannot retrive any further images from inside. So, we look at the details of the `mise_en_abyme_base.jpg` by using `exiftool` on it. We then see a comment as follows
```
Comment                         : c2lrZXlvdXRob3VnaHQK
```
Observe that the code is in base64, so decode it from base64 to standard output

```
$ echo "c2lrZXlvdXRob3VnaHQK" | base64 -d
sikeyouthought
```

- Step 4: We note the key obtained `sikeyouthought`. We then proceed to try other steganography tools on it and by using `steghide` we will realise that there is a file hidden inside the `mise_en_abyme_base.jpg`

```
$ steghide extract -sf mise_en_abyme_base.jpg 
Enter passphrase: 
wrote extracted data to "drawing.flag.svg".
```

- Step 5: Now we observe the `drawing.flag.svg ` file. We see the contents of the file using `cat` and when we closely observe, we see the flag is hidden within the svg file. 

```
$ cat drawing.flag.svg 
```
The file contents are as following:
![Step_1_binwalk_output](solution_images/flag_svg.png)


If we read the file carefully we can see the Letters `M `, `A `, `Z `, `E `, `{P 1 4 a 5 e` etc occuring in a pattern in file before the `</tspan>`  tag.

We can either manually copy the flag from here and remove the spaces between letters or We can extract the flag using the following command:
```
$ cat drawing.flag.svg | grep "</tspan" | cut  -d ">" -f2 | cut -d "<" -f1 |tr -d "\n" | tr -d " "
MAZE{P14a5e13n20tI9n20t15oA1b2y19s19}
```


