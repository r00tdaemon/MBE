```
Dump of assembler code for function check:
   0x08048484 <+0>:     push   ebp
   0x08048485 <+1>:     mov    ebp,esp
   0x08048487 <+3>:     sub    esp,0x28
   0x0804848a <+6>:     mov    DWORD PTR [ebp-0x8],0x0
   0x08048491 <+13>:    mov    DWORD PTR [ebp-0xc],0x0
   0x08048498 <+20>:    mov    eax,DWORD PTR [ebp+0x8]
   0x0804849b <+23>:    mov    DWORD PTR [esp],eax
   0x0804849e <+26>:    call   0x8048384 <strlen@plt>
   0x080484a3 <+31>:    cmp    DWORD PTR [ebp-0xc],eax
   0x080484a6 <+34>:    jae    0x80484fb <check+119>
   0x080484a8 <+36>:    mov    eax,DWORD PTR [ebp-0xc]
   0x080484ab <+39>:    add    eax,DWORD PTR [ebp+0x8]
   0x080484ae <+42>:    movzx  eax,BYTE PTR [eax]
   0x080484b1 <+45>:    mov    BYTE PTR [ebp-0xd],al
   0x080484b4 <+48>:    lea    eax,[ebp-0x4]
   0x080484b7 <+51>:    mov    DWORD PTR [esp+0x8],eax
   0x080484bb <+55>:    mov    DWORD PTR [esp+0x4],0x8048638
   0x080484c3 <+63>:    lea    eax,[ebp-0xd]
   0x080484c6 <+66>:    mov    DWORD PTR [esp],eax
   0x080484c9 <+69>:    call   0x80483a4 <sscanf@plt>
   0x080484ce <+74>:    mov    edx,DWORD PTR [ebp-0x4]
   0x080484d1 <+77>:    lea    eax,[ebp-0x8]
   0x080484d4 <+80>:    add    DWORD PTR [eax],edx
   0x080484d6 <+82>:    cmp    DWORD PTR [ebp-0x8],0xf
   0x080484da <+86>:    jne    0x80484f4 <check+112>
   0x080484dc <+88>:    mov    DWORD PTR [esp],0x804863b
   0x080484e3 <+95>:    call   0x8048394 <printf@plt>
   0x080484e8 <+100>:   mov    DWORD PTR [esp],0x0
   0x080484ef <+107>:   call   0x80483b4 <exit@plt>
   0x080484f4 <+112>:   lea    eax,[ebp-0xc]
   0x080484f7 <+115>:   inc    DWORD PTR [eax]
   0x080484f9 <+117>:   jmp    0x8048498 <check+20>
   0x080484fb <+119>:   mov    DWORD PTR [esp],0x8048649
   0x08048502 <+126>:   call   0x8048394 <printf@plt>
   0x08048507 <+131>:   leave  
   0x08048508 <+132>:   ret   
```

```
arg => ebp + 0x8
loc1 => ebp-0x4
loc2 => ebp-0x8 = 0 
i => ebp-0xc = 0
char => ebp-0xd

for (i=0; i < strlen(arg); i++)
{
	char = arg[i];
	sscanf(char, "%d", &loc1);
	loc2 += loc1;
	if (loc2 == 0xf)
		print ("Password OK!");
}
```
password = any number with sum of digits = 15
e.g. 78, 2346 