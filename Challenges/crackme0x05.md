## Crackme0x05

```
Dump of assembler code for function check:
   0x080484c8 <+0>:     push   ebp
   0x080484c9 <+1>:     mov    ebp,esp
   0x080484cb <+3>:     sub    esp,0x28
   0x080484ce <+6>:     mov    DWORD PTR [ebp-0x8],0x0
   0x080484d5 <+13>:    mov    DWORD PTR [ebp-0xc],0x0
   0x080484dc <+20>:    mov    eax,DWORD PTR [ebp+0x8]
   0x080484df <+23>:    mov    DWORD PTR [esp],eax
   0x080484e2 <+26>:    call   0x8048384 <strlen@plt>
   0x080484e7 <+31>:    cmp    DWORD PTR [ebp-0xc],eax
   0x080484ea <+34>:    jae    0x8048532 <check+106>
   0x080484ec <+36>:    mov    eax,DWORD PTR [ebp-0xc]
   0x080484ef <+39>:    add    eax,DWORD PTR [ebp+0x8]
   0x080484f2 <+42>:    movzx  eax,BYTE PTR [eax]
   0x080484f5 <+45>:    mov    BYTE PTR [ebp-0xd],al
   0x080484f8 <+48>:    lea    eax,[ebp-0x4]
   0x080484fb <+51>:    mov    DWORD PTR [esp+0x8],eax
   0x080484ff <+55>:    mov    DWORD PTR [esp+0x4],0x8048668
   0x08048507 <+63>:    lea    eax,[ebp-0xd]
   0x0804850a <+66>:    mov    DWORD PTR [esp],eax
   0x0804850d <+69>:    call   0x80483a4 <sscanf@plt>
   0x08048512 <+74>:    mov    edx,DWORD PTR [ebp-0x4]
   0x08048515 <+77>:    lea    eax,[ebp-0x8]
   0x08048518 <+80>:    add    DWORD PTR [eax],edx
   0x0804851a <+82>:    cmp    DWORD PTR [ebp-0x8],0x10
   0x0804851e <+86>:    jne    0x804852b <check+99>
   0x08048520 <+88>:    mov    eax,DWORD PTR [ebp+0x8]
   0x08048523 <+91>:    mov    DWORD PTR [esp],eax
   0x08048526 <+94>:    call   0x8048484 <parell>
   0x0804852b <+99>:    lea    eax,[ebp-0xc]
   0x0804852e <+102>:   inc    DWORD PTR [eax]
   0x08048530 <+104>:   jmp    0x80484dc <check+20>
   0x08048532 <+106>:   mov    DWORD PTR [esp],0x8048679
   0x08048539 <+113>:   call   0x8048394 <printf@plt>
   0x0804853e <+118>:   leave  
   0x0804853f <+119>:   ret
```
same as crackme0x04 but sum of digits should be 0x10 (16)

```
Dump of assembler code for function parell:
   0x08048484 <+0>:     push   ebp
   0x08048485 <+1>:     mov    ebp,esp
   0x08048487 <+3>:     sub    esp,0x18
   0x0804848a <+6>:     lea    eax,[ebp-0x4]
   0x0804848d <+9>:     mov    DWORD PTR [esp+0x8],eax
   0x08048491 <+13>:    mov    DWORD PTR [esp+0x4],0x8048668
   0x08048499 <+21>:    mov    eax,DWORD PTR [ebp+0x8]
   0x0804849c <+24>:    mov    DWORD PTR [esp],eax
   0x0804849f <+27>:    call   0x80483a4 <sscanf@plt>
   0x080484a4 <+32>:    mov    eax,DWORD PTR [ebp-0x4]
   0x080484a7 <+35>:    and    eax,0x1
   0x080484aa <+38>:    test   eax,eax
   0x080484ac <+40>:    jne    0x80484c6 <parell+66>
   0x080484ae <+42>:    mov    DWORD PTR [esp],0x804866b
   0x080484b5 <+49>:    call   0x8048394 <printf@plt>
   0x080484ba <+54>:    mov    DWORD PTR [esp],0x0
   0x080484c1 <+61>:    call   0x80483b4 <exit@plt>
   0x080484c6 <+66>:    leave  
   0x080484c7 <+67>:    ret  
```
```
arg -> ebp+0x8 (user i/p)
int loc1 -> ebp-0x4

sscanf(arg, "%d", &loc1);

//..........
eax = loc1
eax = eax & 0x1  // take lsb
if (eax==0)
	print "Password OK!"

//	OR

if (loc1%2 == 0)
	print "Passsword OK!"
```

Therefore password is any **even number with sum = 16**
e.g. 88, 4444, 2356
