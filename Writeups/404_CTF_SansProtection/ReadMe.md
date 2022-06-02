Before we start you need to download the binary from here : [Binary](./fragile).

Here we go let's start by running the binary and see what we have : 

````console
(ironbyte㉿IronByte)-[/mnt/c/Users/IR0NYTE/Desktop/ctf]
└─$ ./fragile
Montrez-nous de quoi vous êtes capable !
Cadeau : 0x7fff8ec7ec20
Asslema ya hmema
````
As you can see the binary gave us some random memory adresse with a beautiful hello in *french*. Why don't we start by checking the architecture of the binary with : 
```console
(ironbyte㉿IronByte)-[/mnt/c/Users/IR0NYTE/Desktop/ctf]
└─$ file fragile
```
We got : 

````bash
fragile: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=6a457609506482cdebb144dbacd9c1f6fba34955, stripped
````
As we can see the architecture of the binary is 0x64 bit, it's also dynamically linked and not striped. Let's try checking out the mitigations that is ON : 

````console
(ironbyte㉿IronByte)-[/mnt/c/Users/IR0NYTE/Desktop/ctf]
└─$ pwn checksec fragile
````
We got : 

````bash 
[*] '/mnt/c/Users/IR0NYTE/Desktop/ctf/fragile'
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX disabled
    PIE:      No PIE (0x400000)
    RWX:      Has RWX segments
````


