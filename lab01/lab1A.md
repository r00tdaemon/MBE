## Lab1A

```
Dump of assembler code for function main:
   0x08048b44 <+0>:     push   ebp
   0x08048b45 <+1>:     mov    ebp,esp
   0x08048b47 <+3>:     and    esp,0xfffffff0
   0x08048b4a <+6>:     sub    esp,0x40
   0x08048b4d <+9>:     mov    eax,DWORD PTR [ebp+0xc]
   0x08048b50 <+12>:    mov    DWORD PTR [esp+0xc],eax
   0x08048b54 <+16>:    mov    eax,gs:0x14
   0x08048b5a <+22>:    mov    DWORD PTR [esp+0x3c],eax
   0x08048b5e <+26>:    xor    eax,eax
   0x08048b60 <+28>:    push   eax
   0x08048b61 <+29>:    xor    eax,eax
   0x08048b63 <+31>:    je     0x8048b68 <main+36>
   0x08048b65 <+33>:    add    esp,0x4
   0x08048b68 <+36>:    pop    eax
   0x08048b69 <+37>:    mov    DWORD PTR [esp],0x8048d73
   0x08048b70 <+44>:    call   0x8048810 <puts@plt>
   0x08048b75 <+49>:    mov    DWORD PTR [esp],0x8048d91
   0x08048b7c <+56>:    call   0x8048810 <puts@plt>
   0x08048b81 <+61>:    mov    DWORD PTR [esp],0x8048daf
   0x08048b88 <+68>:    call   0x8048810 <puts@plt>
   0x08048b8d <+73>:    mov    DWORD PTR [esp],0x8048dcd
   0x08048b94 <+80>:    call   0x8048810 <puts@plt>
   0x08048b99 <+85>:    mov    DWORD PTR [esp],0x8048deb
   0x08048ba0 <+92>:    call   0x8048810 <puts@plt>
   0x08048ba5 <+97>:    mov    DWORD PTR [esp],0x8048e09
   0x08048bac <+104>:   call   0x8048810 <puts@plt>
   0x08048bb1 <+109>:   mov    eax,ds:0x804b060
   0x08048bb6 <+114>:   mov    DWORD PTR [esp+0x8],eax
   0x08048bba <+118>:   mov    DWORD PTR [esp+0x4],0x20
   0x08048bc2 <+126>:   lea    eax,[esp+0x1c]
   0x08048bc6 <+130>:   mov    DWORD PTR [esp],eax
   0x08048bc9 <+133>:   call   0x80487d0 <fgets@plt>
   0x08048bce <+138>:   mov    DWORD PTR [esp],0x8048d73
   0x08048bd5 <+145>:   call   0x8048810 <puts@plt>
   0x08048bda <+150>:   mov    DWORD PTR [esp],0x8048e27
   0x08048be1 <+157>:   call   0x8048810 <puts@plt>
   0x08048be6 <+162>:   mov    DWORD PTR [esp],0x8048dcd
   0x08048bed <+169>:   call   0x8048810 <puts@plt>
   0x08048bf2 <+174>:   mov    DWORD PTR [esp],0x8048e45
   0x08048bf9 <+181>:   call   0x8048810 <puts@plt>
   0x08048bfe <+186>:   mov    DWORD PTR [esp],0x8048e09
   0x08048c05 <+193>:   call   0x8048810 <puts@plt>
   0x08048c0a <+198>:   lea    eax,[esp+0x18]
   0x08048c0e <+202>:   mov    DWORD PTR [esp+0x4],eax
   0x08048c12 <+206>:   mov    DWORD PTR [esp],0x8048d00
   0x08048c19 <+213>:   call   0x8048860 <__isoc99_scanf@plt>
   0x08048c1e <+218>:   mov    eax,DWORD PTR [esp+0x18]
   0x08048c22 <+222>:   mov    DWORD PTR [esp+0x4],eax
   0x08048c26 <+226>:   lea    eax,[esp+0x1c]
   0x08048c2a <+230>:   mov    DWORD PTR [esp],eax
   0x08048c2d <+233>:   call   0x8048a0f <auth>
   0x08048c32 <+238>:   test   eax,eax
   0x08048c34 <+240>:   jne    0x8048c55 <main+273>
   0x08048c36 <+242>:   mov    DWORD PTR [esp],0x8048e63
   0x08048c3d <+249>:   call   0x8048810 <puts@plt>
   0x08048c42 <+254>:   mov    DWORD PTR [esp],0x8048e72
   0x08048c49 <+261>:   call   0x8048820 <system@plt>
   0x08048c4e <+266>:   mov    eax,0x0
   0x08048c53 <+271>:   jmp    0x8048c5a <main+278>
   0x08048c55 <+273>:   mov    eax,0x1
   0x08048c5a <+278>:   mov    edx,DWORD PTR [esp+0x3c]
   0x08048c5e <+282>:   xor    edx,DWORD PTR gs:0x14
   0x08048c65 <+289>:   je     0x8048c6c <main+296>
   0x08048c67 <+291>:   call   0x8048800 <__stack_chk_fail@plt>
   0x08048c6c <+296>:   leave  
   0x08048c6d <+297>:   ret    

```

```
auth(username, serial)
```

```
Dump of assembler code for function auth:
   0x08048a0f <+0>:     push   ebp
   0x08048a10 <+1>:     mov    ebp,esp
   0x08048a12 <+3>:     sub    esp,0x28
   0x08048a15 <+6>:     mov    DWORD PTR [esp+0x4],0x8048d03
   0x08048a1d <+14>:    mov    eax,DWORD PTR [ebp+0x8]
   0x08048a20 <+17>:    mov    DWORD PTR [esp],eax
   0x08048a23 <+20>:    call   0x80487a0 <strcspn@plt>
   0x08048a28 <+25>:    mov    edx,DWORD PTR [ebp+0x8]
   0x08048a2b <+28>:    add    eax,edx
   0x08048a2d <+30>:    mov    BYTE PTR [eax],0x0
   0x08048a30 <+33>:    mov    DWORD PTR [esp+0x4],0x20
   0x08048a38 <+41>:    mov    eax,DWORD PTR [ebp+0x8]
   0x08048a3b <+44>:    mov    DWORD PTR [esp],eax
   0x08048a3e <+47>:    call   0x8048850 <strnlen@plt>
   0x08048a43 <+52>:    mov    DWORD PTR [ebp-0xc],eax
   0x08048a46 <+55>:    push   eax
   0x08048a47 <+56>:    xor    eax,eax
   0x08048a49 <+58>:    je     0x8048a4e <auth+63>
   0x08048a4b <+60>:    add    esp,0x4
   0x08048a4e <+63>:    pop    eax
   0x08048a4f <+64>:    cmp    DWORD PTR [ebp-0xc],0x5
   0x08048a53 <+68>:    jg     0x8048a5f <auth+80>
   0x08048a55 <+70>:    mov    eax,0x1
   0x08048a5a <+75>:    jmp    0x8048b42 <auth+307>
   0x08048a5f <+80>:    mov    DWORD PTR [esp+0xc],0x0
   0x08048a67 <+88>:    mov    DWORD PTR [esp+0x8],0x1
   0x08048a6f <+96>:    mov    DWORD PTR [esp+0x4],0x0
   0x08048a77 <+104>:   mov    DWORD PTR [esp],0x0
   0x08048a7e <+111>:   call   0x8048870 <ptrace@plt>
   0x08048a83 <+116>:   cmp    eax,0xffffffff
   0x08048a86 <+119>:   jne    0x8048ab6 <auth+167>
   0x08048a88 <+121>:   mov    DWORD PTR [esp],0x8048d08
   0x08048a8f <+128>:   call   0x8048810 <puts@plt>
   0x08048a94 <+133>:   mov    DWORD PTR [esp],0x8048d2c
   0x08048a9b <+140>:   call   0x8048810 <puts@plt>
   0x08048aa0 <+145>:   mov    DWORD PTR [esp],0x8048d50
   0x08048aa7 <+152>:   call   0x8048810 <puts@plt>
   0x08048aac <+157>:   mov    eax,0x1
   0x08048ab1 <+162>:   jmp    0x8048b42 <auth+307>
   0x08048ab6 <+167>:   mov    eax,DWORD PTR [ebp+0x8]
   0x08048ab9 <+170>:   add    eax,0x3
   0x08048abc <+173>:   movzx  eax,BYTE PTR [eax]
   0x08048abf <+176>:   movsx  eax,al
   0x08048ac2 <+179>:   xor    eax,0x1337
   0x08048ac7 <+184>:   add    eax,0x5eeded
   0x08048acc <+189>:   mov    DWORD PTR [ebp-0x10],eax
   0x08048acf <+192>:   mov    DWORD PTR [ebp-0x14],0x0
   0x08048ad6 <+199>:   jmp    0x8048b26 <auth+279>
   0x08048ad8 <+201>:   mov    edx,DWORD PTR [ebp-0x14]
   0x08048adb <+204>:   mov    eax,DWORD PTR [ebp+0x8]
   0x08048ade <+207>:   add    eax,edx
   0x08048ae0 <+209>:   movzx  eax,BYTE PTR [eax]
   0x08048ae3 <+212>:   cmp    al,0x1f
   0x08048ae5 <+214>:   jg     0x8048aee <auth+223>
   0x08048ae7 <+216>:   mov    eax,0x1
   0x08048aec <+221>:   jmp    0x8048b42 <auth+307>
   0x08048aee <+223>:   mov    edx,DWORD PTR [ebp-0x14]
   0x08048af1 <+226>:   mov    eax,DWORD PTR [ebp+0x8]
   0x08048af4 <+229>:   add    eax,edx
   0x08048af6 <+231>:   movzx  eax,BYTE PTR [eax]
   0x08048af9 <+234>:   movsx  eax,al
   0x08048afc <+237>:   xor    eax,DWORD PTR [ebp-0x10]
   0x08048aff <+240>:   mov    ecx,eax
   0x08048b01 <+242>:   mov    edx,0x88233b2b
   0x08048b06 <+247>:   mov    eax,ecx
   0x08048b08 <+249>:   mul    edx
   0x08048b0a <+251>:   mov    eax,ecx
   0x08048b0c <+253>:   sub    eax,edx
   0x08048b0e <+255>:   shr    eax,1
   0x08048b10 <+257>:   add    eax,edx
   0x08048b12 <+259>:   shr    eax,0xa
   0x08048b15 <+262>:   imul   eax,eax,0x539
   0x08048b1b <+268>:   sub    ecx,eax
   0x08048b1d <+270>:   mov    eax,ecx
   0x08048b1f <+272>:   add    DWORD PTR [ebp-0x10],eax
   0x08048b22 <+275>:   add    DWORD PTR [ebp-0x14],0x1
   0x08048b26 <+279>:   mov    eax,DWORD PTR [ebp-0x14]
   0x08048b29 <+282>:   cmp    eax,DWORD PTR [ebp-0xc]
   0x08048b2c <+285>:   jl     0x8048ad8 <auth+201>
   0x08048b2e <+287>:   mov    eax,DWORD PTR [ebp+0xc]
   0x08048b31 <+290>:   cmp    eax,DWORD PTR [ebp-0x10]
   0x08048b34 <+293>:   je     0x8048b3d <auth+302>
   0x08048b36 <+295>:   mov    eax,0x1
   0x08048b3b <+300>:   jmp    0x8048b42 <auth+307>
   0x08048b3d <+302>:   mov    eax,0x0
   0x08048b42 <+307>:   leave  
   0x08048b43 <+308>:   ret    
```
```
strcspn(username, "\n")  // will give length of username
loc3 = strlen(username)
if loc3 <= 0x5
	return 1

if (ptrace(0,0,1,0) == -1)
	return 1





```
### short solution
```
gdb-peda$ b *0x08048a83
Breakpoint 1 at 0x8048a83
gdb-peda$ commands 1
Type commands for breakpoint(s) 1, one per line.
End with a line saying just "end".
>set ($eax) = 0
>continue
>end
gdb-peda$ b *0x08048b31
Breakpoint 2 at 0x8048b31
gdb-peda$ r

< enter username and serial >

Breakpoint 2, 0x08048b31 in auth ()
gdb-peda$ x/d $ebp-0x10
0xbffff698:     6230693
```

**for username "admin1" serial is 6230693.**

**flag for this level - `1uCKy_Gue55`**

***

### Original Source

```
/*
Modern Binary Exploitation
Lab 1: Introduction to Reverse Engineering
LabA: Keygen
gcc -s -m32 ./labA.c
*/

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/ptrace.h>
#include <unistd.h>

#include "utils.h"
#define ANSI_COLOR_RED     "\x1b[31m"
#define ANSI_COLOR_GREEN   "\x1b[32m"
#define ANSI_COLOR_YELLOW  "\x1b[33m"

ENABLE_TIMEOUT(60)

int auth(char * username, unsigned int serial) {
    int i, len;
    unsigned int chk;

    username[strcspn(username, "\n")] = 0;
    len = strnlen(username, 32);

    deathrays;
    if (len < 6) {
        return 1;
    }

    if (ptrace(PTRACE_TRACEME, 0, 1, 0) == -1)
    {
        printf(ANSI_COLOR_GREEN ".---------------------------.\n");
        printf(ANSI_COLOR_RED   "| !! TAMPERING DETECTED !!  |\n");
        printf(ANSI_COLOR_GREEN "'---------------------------'\n");

        return 1;
    }

    chk = (username[3] ^ 0x1337) + 0x5EEDED;
    for(i=0; i<len; i++) {
        if (username[i] < 32 || username[i] > 127) {
            return 1;
        }
        chk += (username[i] ^ chk) % 1337;
    }

    if (serial != chk) {
        return 1;
    }

    return 0;
}

int main(int argc, char ** argv) {
    unsigned int serial;
    char username[32];

    deathrays;
    printf(".---------------------------.\n");
    printf("|---------  RPISEC  --------|\n");
    printf("|+ SECURE LOGIN SYS v. 3.0 +|\n");
    printf("|---------------------------|\n");

    printf("|~- Enter your Username:  ~-|\n");
    printf("'---------------------------'\n");
    fgets(username, 32, stdin);

    printf(".---------------------------.\n");
    printf("| !! NEW ACCOUNT DETECTED !!|\n");
    printf("|---------------------------|\n");
    printf("|~- Input your serial:    ~-|\n");
    printf("'---------------------------'\n");
    scanf("%u", &serial);

    if(!auth(username, serial)) {
        printf("Authenticated!\n");
        system("/bin/sh");
        return EXIT_SUCCESS;
    }

    return EXIT_FAILURE;
}
```
