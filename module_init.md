
To facilitate module init undefine the init module section generation so the module init function placed in the ```.text``` section.

```
#undef __init
#define __init
```

```
#0  redirfs_register_filter (info=0xffffffffc001b0a0) at /work/redirfs/src/redirfs/rfs_flt.c:115
#1  0xffffffffc001925b in dummyflt_init () at /work/redirfs/src/dummyflt/dummyflt.c:236
#2  0xffffffff81002193 in do_one_initcall (fn=0xffffffffc0019230 <dummyflt_init>) at ../init/main.c:795
#3  0xffffffff811a35c1 in do_init_module (mod=0xffffffffc001b0c0) at ../kernel/module.c:3421
#4  0xffffffff81111dd2 in load_module (info=0xffffc90000783ea8, uargs=<optimised out>, flags=<optimised out>) at ../kernel/module.c:3743
#5  0xffffffff8111240f in SYSC_finit_module (fd=3, uargs=0x5566f7c833d9 "", flags=0) at ../kernel/module.c:3842
#6  0xffffffff8111245e in SyS_finit_module (fd=<optimised out>, uargs=<optimised out>, flags=<optimised out>) at ../kernel/module.c:3818
#7  0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
#8  0x0000000000000000 in ?? ()
```
