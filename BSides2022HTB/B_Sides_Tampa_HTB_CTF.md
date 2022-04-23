B SIDES TAMPA HACK THE BOX CTF 2022
======
  Team Name: WCSC 5URPR15E
  
  Instructions
  ------
  
  This was the only forensics challange during the competition, At the time of completion the challange was worth roughly 500 points. The prompt is that this is a file
  is responsible for setting up the new vpn for the buisness. So lets download it and see what we get.
  
  Upon Download this is what we recive:
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i1.PNG "image1")
  
  This is a simple zip so lets unzip it and see what is inside, when we open it we recive a file that is called vpn_instructions.docm, upon opening the file we see that all it has
  is a document with a png on it that is prompting me to click to enable editing. This is something I should have taken a screenshot of but neglected to.
  
  Going further I do what I always do in a forensics challange I run a binwalk command on the file: 
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i2.PNG "image2")
  
  Upon completion of the binwalk we open the extracted zip: 
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i22.PNG "image3")
  
  We open the zip to see what is inside of it to see what is inside, we see that there are a few few new directories: 
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i4.PNG "image4")
  The main one of note here is the word directory due to the fact that this is a docm file, a docm file is something that can run a macro on opening, so we need to find the 
  file where the macro is saved.
  
  Opening the word directory, we find the file that we are looking for, the vbaProject.bin
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i5.PNG "img4")
  running a cat on the file we come across a section that is really intresting to me.
  We see that there is a part of the file that matches the flag format->
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i6.PNG "img 6")
  
  So what I decide to do is move it to a .txt file so that I can read the formatting a bit better, so first i use olevba to extract it to the text file then I read it to see the python script:
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i7.PNG "img9")
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i8.PNG "img7")
  Looking at it like this we see that will eventually have the final section appended with a d00r
  
  So, feeding the first section into visual studio code we get this output: 
  ![alt text](https://github.com/Dew-ey/Writeups/blob/main/BSides2022HTB/Instructions/i10.PNG "img8")
  
  Finally putting the two together we get the flag: `HTB{n3w_VPN_n3w_b4ckd00r}`
  
  
  
