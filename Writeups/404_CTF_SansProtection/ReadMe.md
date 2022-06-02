Before we start you need to download the binary from here : [Binary](./fragile).

Here we go, let's start by checking the architecture of the binary with : 
```console
(ironbyte㉿IronByte)-[/mnt/c/Users/IR0NYTE/Desktop/ctf]
└─$ file fragile
```
We get : 

````bash
fragile: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=6a457609506482cdebb144dbacd9c1f6fba34955, stripped
````
As we can see the architecture of the binary 0x64 bit, it's also dynamically linked and not striped. Let's try checking out the mitigations on this binary : 

````console
(ironbyte㉿IronByte)-[/mnt/c/Users/IR0NYTE/Desktop/ctf]
└─$ pwn checksec fragile
````

