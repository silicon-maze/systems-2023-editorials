
# **The Enchanted Layers**

Category: Miscellaneous

Author: Md Arfath

 Flag: MAZE{SKYW4LK3R_V4D3R.} 


## Problem Statement
- Across stellar maps and hidden layers, where intentions veil like the Force, journey forth to triumph.


## Relevant files / links
- [Themap](https://drive.google.com/file/d/1Pq4T7wvjLH5kgIdlZrHBNxcIaNmOqvzF/view?usp=sharing)

## Hint
- Find hidden wisdom, like Jedi between layers.
- Overriding secrets as you navigate.



## Solution
- This file is a .png image, but we need to convert it to a tar file in order to extract its contents. To do this, we can use a file conversion tool or rename the file with a .tar extension and extract it using a tar utility.
- The given file is a tar archive. After extraction, we see many folders of layers with SHA hash names & manifest.json. This is the standard format of a docker image. This image file has to be loaded as an image.

- On looking at the image history you find a file being deleted and a file being added  or Use tool such as Docker Dive to explore layer contents
 - `ADD secret_scroll /usr/local`
 - `ENTRYPOINT ["/bin/sh", "-c", "rm /StarWars/Dagobah/Endor/c && /bin/sh"]`

- Enter into the container  and navigate to /usr/local , on looking at the content of secret_scroll file you get first  half of the flag 
  
- Run a new container with a --entrypoint flag to over-ride the default one   

- ```bash
   Docker run -it --entrypoint=/bin/sh <image-name>
  ```
  
 - The file `c` is a compressed file , use `gunzip` to uncompress it. On looking at the content of the file u get the otherhalf of the flag  
 
 

  Note = By default the used docker image doesnt consist `file` cmd
