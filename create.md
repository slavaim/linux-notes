
```
#0  ext4_create (dir=0xffff88001ce0f708, dentry=0xffff88001cd97540, mode=33206, excl=false) at ../fs/ext4/namei.c:2403
#1  0xffffffff8124931e in lookup_open (opened=<optimised out>, got_write=<optimised out>, op=<optimised out>, file=<optimised out>, path=<optimised out>, nd=<optimised out>) at ../fs/namei.c:3200
#2  do_last (opened=<optimised out>, op=<optimised out>, file=<optimised out>, nd=<optimised out>) at ../fs/namei.c:3291
#3  path_openat (nd=0xffffc9000028fdc0, op=0xffffc9000028fef4, flags=<optimised out>) at ../fs/namei.c:3520
#4  0xffffffff8124a739 in do_filp_open (dfd=<optimised out>, pathname=<optimised out>, op=0xffffc9000028fef4) at ../fs/namei.c:3555
#5  0xffffffff81236974 in do_sys_open (dfd=-100, filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1055
#6  0xffffffff81236a7e in SYSC_open (mode=<optimised out>, flags=<optimised out>, filename=<optimised out>) at ../fs/open.c:1073
#7  SyS_open (filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1068
#8  0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```
