
```
#0  ext4_setattr (dentry=0xffff88001ace2a80, attr=0xffffc90000a77e78) at ../fs/ext4/inode.c:5259
#1  0xffffffff8125982b in notify_change (dentry=0xffff88001ace2a80, attr=0xffffc90000a77e78, delegated_inode=<optimised out>) at ../fs/attr.c:312
#2  0xffffffff81234c38 in chmod_common (path=0xffffc90000a77f08, mode=<optimised out>) at ../fs/open.c:532
#3  0xffffffff8123606a in SYSC_fchmodat (mode=<optimised out>, filename=<optimised out>, dfd=<optimised out>) at ../fs/open.c:565
#4  SyS_fchmodat (dfd=<optimised out>, filename=-60473128550792, mode=<optimised out>) at ../fs/open.c:557
#5  0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```
