## Crackme0x01

```
080483e4 <main>:
 80483e4:       55                      push   ebp
 80483e5:       89 e5                   mov    ebp,esp
 80483e7:       83 ec 18                sub    esp,0x18
 80483ea:       83 e4 f0                and    esp,0xfffffff0
 80483ed:       b8 00 00 00 00          mov    eax,0x0
 80483f2:       83 c0 0f                add    eax,0xf
 80483f5:       83 c0 0f                add    eax,0xf
 80483f8:       c1 e8 04                shr    eax,0x4
 80483fb:       c1 e0 04                shl    eax,0x4
 80483fe:       29 c4                   sub    esp,eax
 8048400:       c7 04 24 28 85 04 08    mov    DWORD PTR [esp],0x8048528
 8048407:       e8 10 ff ff ff          call   804831c <printf@plt>
 804840c:       c7 04 24 41 85 04 08    mov    DWORD PTR [esp],0x8048541
 8048413:       e8 04 ff ff ff          call   804831c <printf@plt>
 8048418:       8d 45 fc                lea    eax,[ebp-0x4]
 804841b:       89 44 24 04             mov    DWORD PTR [esp+0x4],eax
 804841f:       c7 04 24 4c 85 04 08    mov    DWORD PTR [esp],0x804854c
 8048426:       e8 e1 fe ff ff          call   804830c <scanf@plt>
 804842b:       81 7d fc 9a 14 00 00    cmp    DWORD PTR [ebp-0x4],0x149a
 8048432:       74 0e                   je     8048442 <main+0x5e>
 8048434:       c7 04 24 4f 85 04 08    mov    DWORD PTR [esp],0x804854f
 804843b:       e8 dc fe ff ff          call   804831c <printf@plt>
 8048440:       eb 0c                   jmp    804844e <main+0x6a>
 8048442:       c7 04 24 62 85 04 08    mov    DWORD PTR [esp],0x8048562
 8048449:       e8 ce fe ff ff          call   804831c <printf@plt>
 804844e:       b8 00 00 00 00          mov    eax,0x0
 8048453:       c9                      leave  
 8048454:       c3                      ret    
 8048455:       90                      nop
 8048456:       90                      nop

```

`804842b:` The function compares the value of local variable with 0x149a 

