## Crackme0x06

```
env_var => ebp+0x10
check(input, env_var) 

```
```
if (sum_of_digits == 16)
    parell(input, env_var)
```
```
Dump of assembler code for function parell:
   0x0804851a <+0>:     push   ebp
   0x0804851b <+1>:     mov    ebp,esp
   0x0804851d <+3>:     sub    esp,0x18
   0x08048520 <+6>:     lea    eax,[ebp-0x4]
   0x08048523 <+9>:     mov    DWORD PTR [esp+0x8],eax
   0x08048527 <+13>:    mov    DWORD PTR [esp+0x4],0x804873d
   0x0804852f <+21>:    mov    eax,DWORD PTR [ebp+0x8]
   0x08048532 <+24>:    mov    DWORD PTR [esp],eax
   0x08048535 <+27>:    call   0x80483c8 <sscanf@plt>
   0x0804853a <+32>:    mov    eax,DWORD PTR [ebp+0xc]
   0x0804853d <+35>:    mov    DWORD PTR [esp+0x4],eax
   0x08048541 <+39>:    mov    eax,DWORD PTR [ebp-0x4]
   0x08048544 <+42>:    mov    DWORD PTR [esp],eax
   0x08048547 <+45>:    call   0x80484b4 <dummy>
   0x0804854c <+50>:    test   eax,eax
   0x0804854e <+52>:    je     0x8048586 <parell+108>
   0x08048550 <+54>:    mov    DWORD PTR [ebp-0x8],0x0
   0x08048557 <+61>:    cmp    DWORD PTR [ebp-0x8],0x9
   0x0804855b <+65>:    jg     0x8048586 <parell+108>
   0x0804855d <+67>:    mov    eax,DWORD PTR [ebp-0x4]
   0x08048560 <+70>:    and    eax,0x1
   0x08048563 <+73>:    test   eax,eax
   0x08048565 <+75>:    jne    0x804857f <parell+101>
   0x08048567 <+77>:    mov    DWORD PTR [esp],0x8048740
   0x0804856e <+84>:    call   0x80483b8 <printf@plt>
   0x08048573 <+89>:    mov    DWORD PTR [esp],0x0
   0x0804857a <+96>:    call   0x80483e8 <exit@plt>
   0x0804857f <+101>:   lea    eax,[ebp-0x8]
   0x08048582 <+104>:   inc    DWORD PTR [eax]
   0x08048584 <+106>:   jmp    0x8048557 <parell+61>
   0x08048586 <+108>:   leave  
   0x08048587 <+109>:   ret   
```

```
arg1 => ebp+0x8  // input
arg2 => ebp+0xc  // env_var
int loc1 => ebp-0x4
int i => ebp-0x8
sscanf(arg1, "%d", loc1)
if (dummy(loc1, arg2) != 0)
	for(i=0; i<9; i++)
	{
		if (loc1 & 1 == 0)
			print("password OK")
	}
```

```
Dump of assembler code for function dummy:
   0x080484b4 <+0>:     push   ebp
   0x080484b5 <+1>:     mov    ebp,esp
   0x080484b7 <+3>:     sub    esp,0x18
   0x080484ba <+6>:     mov    DWORD PTR [ebp-0x4],0x0
   0x080484c1 <+13>:    mov    eax,DWORD PTR [ebp-0x4]
   0x080484c4 <+16>:    lea    edx,[eax*4+0x0]
   0x080484cb <+23>:    mov    eax,DWORD PTR [ebp+0xc]
   0x080484ce <+26>:    cmp    DWORD PTR [edx+eax*1],0x0
   0x080484d2 <+30>:    je     0x804850e <dummy+90>
   0x080484d4 <+32>:    mov    eax,DWORD PTR [ebp-0x4]
   0x080484d7 <+35>:    lea    ecx,[eax*4+0x0]
   0x080484de <+42>:    mov    edx,DWORD PTR [ebp+0xc]
   0x080484e1 <+45>:    lea    eax,[ebp-0x4]
   0x080484e4 <+48>:    inc    DWORD PTR [eax]
   0x080484e6 <+50>:    mov    DWORD PTR [esp+0x8],0x3
   0x080484ee <+58>:    mov    DWORD PTR [esp+0x4],0x8048738
   0x080484f6 <+66>:    mov    eax,DWORD PTR [ecx+edx*1]
   0x080484f9 <+69>:    mov    DWORD PTR [esp],eax
   0x080484fc <+72>:    call   0x80483d8 <strncmp@plt>
   0x08048501 <+77>:    test   eax,eax
   0x08048503 <+79>:    jne    0x80484c1 <dummy+13>
   0x08048505 <+81>:    mov    DWORD PTR [ebp-0x8],0x1
   0x0804850c <+88>:    jmp    0x8048515 <dummy+97>
   0x0804850e <+90>:    mov    DWORD PTR [ebp-0x8],0x0
   0x08048515 <+97>:    mov    eax,DWORD PTR [ebp-0x8]
   0x08048518 <+100>:   leave  
   0x08048519 <+101>:   ret 
```

```
arg1=> ebp+0x8  // user input
arg2=> ebp+0xc  // env_var
loc1 => ebp-0x4
loc2 => ebp-0x8

loc1 = 0

edx = 4*loc1;
while (arg2[edx] != 0)
{
  	loc1++
  	if (strncmp(arg2[edx], "LOLO", 3)==0)
  	{
  	    loc2 = 1
  	}
}

return loc2
```

Password is same as crackme0x05 but there should be an env variable statring with "LOL"