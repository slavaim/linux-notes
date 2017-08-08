
```
#0  __lookup_mnt (mnt=0xffff88001f2199a0, dentry=0xffff88001da80d80) at ../fs/namespace.c:629
#1  0xffffffff81244601 in __follow_mount_rcu (path=0xffffc90000a87c18, inode=0xffffc90000a87c10, seqp=0xffffc90000a87c0c, nd=<optimised out>, nd=<optimised out>) at ../fs/namei.c:1307
#2  0xffffffff812453ef in lookup_fast (nd=0xffff88001f2199a0, path=0xffff88001da80d80, inode=0xffffc90000a87c18, seqp=0xffffc90000a87c0c) at ../fs/namei.c:1591
#3  0xffffffff81245d69 in walk_component (nd=0xffff88001f2199a0, flags=497552768) at ../fs/namei.c:1780
#4  0xffffffff8124620f in link_path_walk (name=0xffff88001c629022 "filesystems", nd=0xffff88001da80d80) at ../fs/namei.c:2113
#5  0xffffffff81248147 in path_openat (nd=0xffffc90000a87dc0, op=0xffffc90000a87ef4, flags=<optimised out>) at ../fs/namei.c:3520
#6  0xffffffff8124a739 in do_filp_open (dfd=<optimised out>, pathname=<optimised out>, op=0xffffc90000a87ef4) at ../fs/namei.c:3555
#7  0xffffffff81236974 in do_sys_open (dfd=-100, filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1055
#8  0xffffffff81236a7e in SYSC_open (mode=<optimised out>, flags=<optimised out>, filename=<optimised out>) at ../fs/open.c:1073
#9  SyS_open (filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1068
#10 0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```

```
#0  __lookup_mnt (mnt=0xffff88001f2199a0, dentry=0xffff88001da80b40) at ../fs/namespace.c:629
#1  0xffffffff81244601 in __follow_mount_rcu (path=0xffffc90000a87be8, inode=0xffffc90000a87be0, seqp=0xffffc90000a87bdc, nd=<optimised out>, nd=<optimised out>) at ../fs/namei.c:1307
#2  0xffffffff812453ef in lookup_fast (nd=0xffff88001f2199a0, path=0xffff88001da80b40, inode=0xffffc90000a87be8, seqp=0xffffc90000a87bdc) at ../fs/namei.c:1591
#3  0xffffffff81245d69 in walk_component (nd=0xffff88001f2199a0, flags=497552192) at ../fs/namei.c:1780
#4  0xffffffff8124620f in link_path_walk (name=0xffff88001c629021 "fs/selinux", nd=0xffff88001da80b40) at ../fs/namei.c:2113
#5  0xffffffff8124675c in path_lookupat (nd=0xffffc90000a87d10, flags=0, path=0xffffc90000a87e68) at ../fs/namei.c:2301
#6  0xffffffff81249a28 in filename_lookup (dfd=<optimised out>, name=0xffff88001c629000, flags=11041768, path=0xffffc90000a87be0, root=<optimised out>) at ../fs/namei.c:2336
#7  0xffffffff81249be6 in user_path_at_empty (dfd=-100, name=<optimised out>, flags=5, path=0xffffc90000a87e68, empty=<optimised out>) at ../fs/namei.c:2590
#8  0xffffffff81271396 in user_path_at (path=<optimised out>, flags=<optimised out>, name=<optimised out>, dfd=<optimised out>) at ../include/linux/namei.h:56
#9  user_statfs (pathname=0xffff88001f2199a0 "", st=0xffff88001da80b40) at ../fs/statfs.c:84
#10 0xffffffff81271417 in SYSC_statfs (pathname=<optimised out>, buf=0x7ffd3668dd20) at ../fs/statfs.c:176
#11 0xffffffff8127179e in SyS_statfs (pathname=<optimised out>, buf=<optimised out>) at ../fs/statfs.c:173
#12 0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```
