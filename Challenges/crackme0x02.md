## Crackme0x02

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
 8048400:       c7 04 24 48 85 04 08    mov    DWORD PTR [esp],0x8048548
 8048407:       e8 10 ff ff ff          call   804831c <printf@plt>
 804840c:       c7 04 24 61 85 04 08    mov    DWORD PTR [esp],0x8048561
 8048413:       e8 04 ff ff ff          call   804831c <printf@plt>
 8048418:       8d 45 fc                lea    eax,[ebp-0x4]
 804841b:       89 44 24 04             mov    DWORD PTR [esp+0x4],eax
 804841f:       c7 04 24 6c 85 04 08    mov    DWORD PTR [esp],0x804856c
 8048426:       e8 e1 fe ff ff          call   804830c <scanf@plt>
 804842b:       c7 45 f8 5a 00 00 00    mov    DWORD PTR [ebp-0x8],0x5a
 8048432:       c7 45 f4 ec 01 00 00    mov    DWORD PTR [ebp-0xc],0x1ec
 8048439:       8b 55 f4                mov    edx,DWORD PTR [ebp-0xc]
 804843c:       8d 45 f8                lea    eax,[ebp-0x8]
 804843f:       01 10                   add    DWORD PTR [eax],edx
 8048441:       8b 45 f8                mov    eax,DWORD PTR [ebp-0x8]
 8048444:       0f af 45 f8             imul   eax,DWORD PTR [ebp-0x8]
 8048448:       89 45 f4                mov    DWORD PTR [ebp-0xc],eax
 804844b:       8b 45 fc                mov    eax,DWORD PTR [ebp-0x4]
 804844e:       3b 45 f4                cmp    eax,DWORD PTR [ebp-0xc]
 8048451:       75 0e                   jne    8048461 <main+0x7d>
 8048453:       c7 04 24 6f 85 04 08    mov    DWORD PTR [esp],0x804856f
 804845a:       e8 bd fe ff ff          call   804831c <printf@plt>
 804845f:       eb 0c                   jmp    804846d <main+0x89>
 8048461:       c7 04 24 7f 85 04 08    mov    DWORD PTR [esp],0x804857f
 8048468:       e8 af fe ff ff          call   804831c <printf@plt>
 804846d:       b8 00 00 00 00          mov    eax,0x0
 8048472:       c9                      leave  
 8048473:       c3                      ret    
```

```
804842b: localvar1 = 0x5a									90
8048432: localvar2 = 0x1ec									492
8048439: edx = localvar2									edx = 492
804843c: eax = &localvar1  // addr of localvar1
804843f: *eax = *eax + edx  // value at eax + edx			localvar1 = 90 + 492 = 582
8048441: eax = localvar1									eax = 582
8048444: eax = eax * localvar1								eax = 338724
8048448: localvar2 = eax
804844b: eax = user_input
804844e: compare eax == localvar2
```
 password = 338724
