## Crackme0x03

```
Dump of assembler code for function main:
   0x08048498 <+0>:     push   ebp
   0x08048499 <+1>:     mov    ebp,esp
   0x0804849b <+3>:     sub    esp,0x18
   0x0804849e <+6>:     and    esp,0xfffffff0
   0x080484a1 <+9>:     mov    eax,0x0
   0x080484a6 <+14>:    add    eax,0xf
   0x080484a9 <+17>:    add    eax,0xf
   0x080484ac <+20>:    shr    eax,0x4
   0x080484af <+23>:    shl    eax,0x4
   0x080484b2 <+26>:    sub    esp,eax
   0x080484b4 <+28>:    mov    DWORD PTR [esp],0x8048610
   0x080484bb <+35>:    call   0x8048350 <printf@plt>
   0x080484c0 <+40>:    mov    DWORD PTR [esp],0x8048629
   0x080484c7 <+47>:    call   0x8048350 <printf@plt>
   0x080484cc <+52>:    lea    eax,[ebp-0x4]
   0x080484cf <+55>:    mov    DWORD PTR [esp+0x4],eax
   0x080484d3 <+59>:    mov    DWORD PTR [esp],0x8048634
   0x080484da <+66>:    call   0x8048330 <scanf@plt>
   0x080484df <+71>:    mov    DWORD PTR [ebp-0x8],0x5a
   0x080484e6 <+78>:    mov    DWORD PTR [ebp-0xc],0x1ec
   0x080484ed <+85>:    mov    edx,DWORD PTR [ebp-0xc]
   0x080484f0 <+88>:    lea    eax,[ebp-0x8]
   0x080484f3 <+91>:    add    DWORD PTR [eax],edx
   0x080484f5 <+93>:    mov    eax,DWORD PTR [ebp-0x8]
   0x080484f8 <+96>:    imul   eax,DWORD PTR [ebp-0x8]
   0x080484fc <+100>:   mov    DWORD PTR [ebp-0xc],eax
   0x080484ff <+103>:   mov    eax,DWORD PTR [ebp-0xc]
   0x08048502 <+106>:   mov    DWORD PTR [esp+0x4],eax
   0x08048506 <+110>:   mov    eax,DWORD PTR [ebp-0x4]
   0x08048509 <+113>:   mov    DWORD PTR [esp],eax
   0x0804850c <+116>:   call   0x804846e <test>
   0x08048511 <+121>:   mov    eax,0x0
   0x08048516 <+126>:   leave  
   0x08048517 <+127>:   ret    
```

```
Dump of assembler code for function test:
   0x0804846e <+0>:     push   ebp
   0x0804846f <+1>:     mov    ebp,esp
   0x08048471 <+3>:     sub    esp,0x8
   0x08048474 <+6>:     mov    eax,DWORD PTR [ebp+0x8]
   0x08048477 <+9>:     cmp    eax,DWORD PTR [ebp+0xc]
   0x0804847a <+12>:    je     0x804848a <test+28>
   0x0804847c <+14>:    mov    DWORD PTR [esp],0x80485ec
   0x08048483 <+21>:    call   0x8048414 <shift>
   0x08048488 <+26>:    jmp    0x8048496 <test+40>
   0x0804848a <+28>:    mov    DWORD PTR [esp],0x80485fe
   0x08048491 <+35>:    call   0x8048414 <shift>
   0x08048496 <+40>:    leave  
   0x08048497 <+41>:    ret   
```

```
Dump of assembler code for function shift:
   0x08048414 <+0>:     push   ebp
   0x08048415 <+1>:     mov    ebp,esp
   0x08048417 <+3>:     sub    esp,0x98
   0x0804841d <+9>:     mov    DWORD PTR [ebp-0x7c],0x0
   0x08048424 <+16>:    mov    eax,DWORD PTR [ebp+0x8]
   0x08048427 <+19>:    mov    DWORD PTR [esp],eax
   0x0804842a <+22>:    call   0x8048340 <strlen@plt>
   0x0804842f <+27>:    cmp    DWORD PTR [ebp-0x7c],eax
   0x08048432 <+30>:    jae    0x8048450 <shift+60>
   0x08048434 <+32>:    lea    eax,[ebp-0x78]
   0x08048437 <+35>:    mov    edx,eax
   0x08048439 <+37>:    add    edx,DWORD PTR [ebp-0x7c]
   0x0804843c <+40>:    mov    eax,DWORD PTR [ebp-0x7c]
   0x0804843f <+43>:    add    eax,DWORD PTR [ebp+0x8]
   0x08048442 <+46>:    movzx  eax,BYTE PTR [eax]
   0x08048445 <+49>:    sub    al,0x3
   0x08048447 <+51>:    mov    BYTE PTR [edx],al
   0x08048449 <+53>:    lea    eax,[ebp-0x7c]
   0x0804844c <+56>:    inc    DWORD PTR [eax]
   0x0804844e <+58>:    jmp    0x8048424 <shift+16>
   0x08048450 <+60>:    lea    eax,[ebp-0x78]
   0x08048453 <+63>:    add    eax,DWORD PTR [ebp-0x7c]
   0x08048456 <+66>:    mov    BYTE PTR [eax],0x0
   0x08048459 <+69>:    lea    eax,[ebp-0x78]
   0x0804845c <+72>:    mov    DWORD PTR [esp+0x4],eax
   0x08048460 <+76>:    mov    DWORD PTR [esp],0x80485e8
   0x08048467 <+83>:    call   0x8048350 <printf@plt>
   0x0804846c <+88>:    leave  
   0x0804846d <+89>:    ret
```


