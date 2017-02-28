
Before a shared library fuynction address is being resolved

```
(gdb) disassem 0x00007ffff7bd86b5
Dump of assembler code for function foo:
   0x00007ffff7bd86b5 <+0>:	push   %rbp
   0x00007ffff7bd86b6 <+1>:	mov    %rsp,%rbp
=> 0x00007ffff7bd86b9 <+4>:	lea    0x11(%rip),%rdi        # 0x7ffff7bd86d1
   0x00007ffff7bd86c0 <+11>:	callq  0x7ffff7bd85a0 <puts@plt>
   0x00007ffff7bd86c5 <+16>:	pop    %rbp
   0x00007ffff7bd86c6 <+17>:	retq   
End of assembler dump.
(gdb) disassem 0x7ffff7bd85a0
Dump of assembler code for function puts@plt:
   0x00007ffff7bd85a0 <+0>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x00007ffff7bd85a6 <+6>:	pushq  $0x0
   0x00007ffff7bd85ab <+11>:	jmpq   0x7ffff7bd8590
End of assembler dump.
(gdb) x/gx 0x7ffff7dd9018
0x7ffff7dd9018:	0x00007ffff7bd85a6
(gdb) disassem 0x00007ffff7bd85a6
Dump of assembler code for function puts@plt:
   0x00007ffff7bd85a0 <+0>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x00007ffff7bd85a6 <+6>:	pushq  $0x0
   0x00007ffff7bd85ab <+11>:	jmpq   0x7ffff7bd8590
End of assembler dump.
(gdb) x/gx 0x7ffff7dd9018
0x7ffff7dd9018:	0x00007ffff7bd85a6
(gdb) disassem 0x00007ffff7bd85a6
Dump of assembler code for function puts@plt:
   0x00007ffff7bd85a0 <+0>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x00007ffff7bd85a6 <+6>:	pushq  $0x0
   0x00007ffff7bd85ab <+11>:	jmpq   0x7ffff7bd8590
End of assembler dump.
(gdb) x/gx 0x7ffff7dd9018
0x7ffff7dd9018:	0x00007ffff7bd85a6
(gdb) disassem 0x7ffff7bd8590
No function contains specified address.
(gdb) disassem 0x00007ffff7bd85a6
Dump of assembler code for function puts@plt:
   0x00007ffff7bd85a0 <+0>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x00007ffff7bd85a6 <+6>:	pushq  $0x0
   0x00007ffff7bd85ab <+11>:	jmpq   0x7ffff7bd8590
End of assembler dump.
(gdb) x/10i 0x7ffff7bd8590
   0x7ffff7bd8590:	pushq  0x200a72(%rip)        # 0x7ffff7dd9008
   0x7ffff7bd8596:	jmpq   *0x200a74(%rip)        # 0x7ffff7dd9010
   0x7ffff7bd859c:	nopl   0x0(%rax)
   0x7ffff7bd85a0 <puts@plt>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x7ffff7bd85a6 <puts@plt+6>:	pushq  $0x0
   0x7ffff7bd85ab <puts@plt+11>:	jmpq   0x7ffff7bd8590
   0x7ffff7bd85b0 <__gmon_start__@plt>:	jmpq   *0x200a6a(%rip)        # 0x7ffff7dd9020
   0x7ffff7bd85b6 <__gmon_start__@plt+6>:	pushq  $0x1
   0x7ffff7bd85bb <__gmon_start__@plt+11>:	jmpq   0x7ffff7bd8590
   0x7ffff7bd85c0 <__cxa_finalize@plt>:	jmpq   *0x200a62(%rip)        # 0x7ffff7dd9028
(gdb) x/gx 0x7ffff7dd9010
0x7ffff7dd9010:	0x00007ffff7df04a0
(gdb) disassem 0x00007ffff7df04a0
Dump of assembler code for function _dl_runtime_resolve:
   0x00007ffff7df04a0 <+0>:	sub    $0x38,%rsp
   0x00007ffff7df04a4 <+4>:	mov    %rax,(%rsp)
   0x00007ffff7df04a8 <+8>:	mov    %rcx,0x8(%rsp)
   0x00007ffff7df04ad <+13>:	mov    %rdx,0x10(%rsp)
   0x00007ffff7df04b2 <+18>:	mov    %rsi,0x18(%rsp)
   0x00007ffff7df04b7 <+23>:	mov    %rdi,0x20(%rsp)
   0x00007ffff7df04bc <+28>:	mov    %r8,0x28(%rsp)
   0x00007ffff7df04c1 <+33>:	mov    %r9,0x30(%rsp)
   0x00007ffff7df04c6 <+38>:	mov    0x40(%rsp),%rsi
   0x00007ffff7df04cb <+43>:	mov    0x38(%rsp),%rdi
   0x00007ffff7df04d0 <+48>:	callq  0x7ffff7de9430 <_dl_fixup>
   0x00007ffff7df04d5 <+53>:	mov    %rax,%r11
   0x00007ffff7df04d8 <+56>:	mov    0x30(%rsp),%r9
   0x00007ffff7df04dd <+61>:	mov    0x28(%rsp),%r8
   0x00007ffff7df04e2 <+66>:	mov    0x20(%rsp),%rdi
   0x00007ffff7df04e7 <+71>:	mov    0x18(%rsp),%rsi
   0x00007ffff7df04ec <+76>:	mov    0x10(%rsp),%rdx
   0x00007ffff7df04f1 <+81>:	mov    0x8(%rsp),%rcx
   0x00007ffff7df04f6 <+86>:	mov    (%rsp),%rax
   0x00007ffff7df04fa <+90>:	add    $0x48,%rsp
   0x00007ffff7df04fe <+94>:	jmpq   *%r11
End of assembler dump.
(gdb) 

```

At the time of linking to a shared library

```
(gdb) bt
#0  strcmp () at ../sysdeps/x86_64/multiarch/../strcmp.S:142
#1  0x00007ffff7deb1d4 in _dl_name_match_p (name=0x7ffff7bd83fe "libc.so.6", map=<optimised out>) at dl-misc.c:295
#2  0x00007ffff7de402f in do_lookup_x (new_hash=new_hash@entry=2090629905, old_hash=old_hash@entry=0x7fffffffdcb0, 
    result=result@entry=0x7fffffffdcc0, scope=<optimised out>, i=<optimised out>, i@entry=0, flags=flags@entry=1, skip=skip@entry=0x0, 
    undef_map=undef_map@entry=0x7ffff7ff9520) at dl-lookup.c:462
#3  0x00007ffff7de4961 in _dl_lookup_symbol_x (undef_name=0x7ffff7bd83f9 "puts", undef_map=0x7ffff7ff9520, ref=ref@entry=0x7fffffffdd78, 
    symbol_scope=0x7ffff7ff9878, version=0x7ffff7fcf030, type_class=type_class@entry=1, flags=1, skip_map=skip_map@entry=0x0)
    at dl-lookup.c:737
#4  0x00007ffff7de9527 in _dl_fixup (l=<optimised out>, reloc_arg=<optimised out>) at ../elf/dl-runtime.c:111
#5  0x00007ffff7df04d5 in _dl_runtime_resolve () at ../sysdeps/x86_64/dl-trampoline.S:45
#6  0x00007ffff7bd86c5 in foo () from /work/test/1/shared.o
#7  0x00000000004006f5 in main () at test.c:8
```

After the shared library function address has been resolved

```
(gdb) bt
#0  0x00007ffff7bd86c5 in foo () from /work/test/1/shared.o
#1  0x00000000004006f5 in main () at test.c:8
(gdb) disassem
Dump of assembler code for function foo:
   0x00007ffff7bd86b5 <+0>:	push   %rbp
   0x00007ffff7bd86b6 <+1>:	mov    %rsp,%rbp
   0x00007ffff7bd86b9 <+4>:	lea    0x11(%rip),%rdi        # 0x7ffff7bd86d1
   0x00007ffff7bd86c0 <+11>:	callq  0x7ffff7bd85a0 <puts@plt>
=> 0x00007ffff7bd86c5 <+16>:	pop    %rbp
   0x00007ffff7bd86c6 <+17>:	retq   
End of assembler dump.
(gdb) disassem 0x7ffff7bd85a0
Dump of assembler code for function puts@plt:
   0x00007ffff7bd85a0 <+0>:	jmpq   *0x200a72(%rip)        # 0x7ffff7dd9018
   0x00007ffff7bd85a6 <+6>:	pushq  $0x0
   0x00007ffff7bd85ab <+11>:	jmpq   0x7ffff7bd8590
End of assembler dump.
(gdb) x/gx 0x7ffff7dd9018
0x7ffff7dd9018:	0x00007ffff7882d60
(gdb) disassem 0x00007ffff7882d60
Dump of assembler code for function _IO_puts:
   0x00007ffff7882d60 <+0>:	push   %r12
   0x00007ffff7882d62 <+2>:	mov    %rdi,%r12
   0x00007ffff7882d65 <+5>:	push   %rbp
   0x00007ffff7882d66 <+6>:	push   %rbx
   0x00007ffff7882d67 <+7>:	callq  0x7ffff789b9b0 <strlen>
   0x00007ffff7882d6c <+12>:	mov    0x34fafd(%rip),%rbx        # 0x7ffff7bd2870 <stdout>
   0x00007ffff7882d73 <+19>:	mov    %rax,%rbp
   0x00007ffff7882d76 <+22>:	mov    (%rbx),%eax
   0x00007ffff7882d78 <+24>:	mov    %rbx,%rdi
   0x00007ffff7882d7b <+27>:	and    $0x8000,%eax
```
