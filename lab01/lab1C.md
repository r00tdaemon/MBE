## Lab1C
```
   0x080486ad <+0>:     push   ebp
   0x080486ae <+1>:     mov    ebp,esp
   0x080486b0 <+3>:     and    esp,0xfffffff0
   0x080486b3 <+6>:     sub    esp,0x20
   0x080486b6 <+9>:     mov    DWORD PTR [esp],0x80487d0
   0x080486bd <+16>:    call   0x8048560 <puts@plt>
   0x080486c2 <+21>:    mov    DWORD PTR [esp],0x80487ee
   0x080486c9 <+28>:    call   0x8048560 <puts@plt>
   0x080486ce <+33>:    mov    DWORD PTR [esp],0x80487d0
   0x080486d5 <+40>:    call   0x8048560 <puts@plt>
   0x080486da <+45>:    mov    DWORD PTR [esp],0x804880c
   0x080486e1 <+52>:    call   0x8048550 <printf@plt>
   0x080486e6 <+57>:    lea    eax,[esp+0x1c]
   0x080486ea <+61>:    mov    DWORD PTR [esp+0x4],eax
   0x080486ee <+65>:    mov    DWORD PTR [esp],0x8048818
   0x080486f5 <+72>:    call   0x80485a0 <__isoc99_scanf@plt>
   0x080486fa <+77>:    mov    eax,DWORD PTR [esp+0x1c]
   0x080486fe <+81>:    cmp    eax,0x149a
   0x08048703 <+86>:    jne    0x8048724 <main+119>
   0x08048705 <+88>:    mov    DWORD PTR [esp],0x804881b
   0x0804870c <+95>:    call   0x8048560 <puts@plt>
   0x08048711 <+100>:   mov    DWORD PTR [esp],0x804882b
   0x08048718 <+107>:   call   0x8048570 <system@plt>
   0x0804871d <+112>:   mov    eax,0x0
   0x08048722 <+117>:   jmp    0x8048735 <main+136>
   0x08048724 <+119>:   mov    DWORD PTR [esp],0x8048833
   0x0804872b <+126>:   call   0x8048560 <puts@plt>
   0x08048730 <+131>:   mov    eax,0x1
   0x08048735 <+136>:   leave  
   0x08048736 <+137>:   ret  
```
password = 5274 (0x149a)

password to Lab1B - `n0_str1ngs_n0_pr0bl3m`
