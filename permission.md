
```
#0  generic_permission (inode=0xffff88001db8e498, mask=1) at ../fs/namei.c:337
#1  0xffffffff812afc1d in proc_pid_permission (inode=0xffff88001db8e498, mask=1) at ../fs/proc/base.c:721
#2  0xffffffff812441f7 in do_inode_permission (mask=<optimised out>, inode=<optimised out>) at ../fs/namei.c:382
#3  __inode_permission (inode=0xffff88001db8e498, mask=1) at ../fs/namei.c:424
#4  0xffffffff81244264 in inode_permission (inode=<optimised out>, mask=<optimised out>) at ../fs/namei.c:475
#5  0xffffffff81246370 in may_lookup (nd=<optimised out>) at ../fs/namei.c:1676
#6  link_path_walk (name=0xffff88001d1cb026 "cgroup", nd=0xffffc900000d7dc0) at ../fs/namei.c:2056
#7  0xffffffff81248147 in path_openat (nd=0xffffc900000d7dc0, op=0xffffc900000d7ef4, flags=<optimised out>) at ../fs/namei.c:3520
#8  0xffffffff8124a739 in do_filp_open (dfd=<optimised out>, pathname=<optimised out>, op=0xffffc900000d7ef4) at ../fs/namei.c:3555
#9  0xffffffff81236974 in do_sys_open (dfd=-100, filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1055
#10 0xffffffff81236a7e in SYSC_open (mode=<optimised out>, flags=<optimised out>, filename=<optimised out>) at ../fs/open.c:1073
#11 SyS_open (filename=<optimised out>, flags=<optimised out>, mode=<optimised out>) at ../fs/open.c:1068
#12 0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```

```
#0  generic_permission (inode=0xffff88001dae8520, mask=129) at ../fs/namei.c:337
#1  0xffffffff812441ab in do_inode_permission (mask=<optimised out>, inode=<optimised out>) at ../fs/namei.c:389
#2  __inode_permission (inode=0xffff88001dae8520, mask=129) at ../fs/namei.c:424
#3  0xffffffff81244264 in inode_permission (inode=<optimised out>, mask=<optimised out>) at ../fs/namei.c:475
#4  0xffffffff812460f5 in may_lookup (nd=<optimised out>) at ../fs/namei.c:1670
#5  link_path_walk (name=0xffff88001d1cb01d "run/systemd/notify", nd=0x81 <irq_stack_union+129>) at ../fs/namei.c:2056
#6  0xffffffff8124675c in path_lookupat (nd=0xffffc900005a3ab0, flags=0, path=0xffffc900005a3c10) at ../fs/namei.c:2301
#7  0xffffffff81249a28 in filename_lookup (dfd=<optimised out>, name=0xffff88001d1cb000, flags=0, path=0x2 <irq_stack_union+2>, root=<optimised out>) at ../fs/namei.c:2336
#8  0xffffffff81249b3b in kern_path (name=<optimised out>, flags=1, path=0xffffc900005a3c10) at ../fs/namei.c:2425
#9  0xffffffff8183c7a5 in unix_find_other (net=<optimised out>, sunname=<optimised out>, len=<optimised out>, type=2, hash=<optimised out>, error=0x746f6e2f646d6574) at ../net/unix/af_unix.c:914
#10 0xffffffff8183d479 in unix_dgram_sendmsg (sock=0xffff88001dbe2d00, msg=<optimised out>, len=10) at ../net/unix/af_unix.c:1721
#11 0xffffffff8176de18 in sock_sendmsg_nosec (msg=<optimised out>, sock=<optimised out>) at ../net/socket.c:633
#12 sock_sendmsg (sock=0xffff88001dbe2d00, msg=0xffffc900005a3ec0) at ../net/socket.c:643
#13 0xffffffff8176e8f6 in ___sys_sendmsg (sock=0xffff88001dbe2d00, msg=<optimised out>, msg_sys=0xffffc900005a3ec0, flags=<optimised out>, used_address=<optimised out>, 
    allowed_msghdr_flags=<optimised out>) at ../net/socket.c:1997
#14 0xffffffff8176f294 in __sys_sendmsg (fd=<optimised out>, msg=0x7ffc902d2f30, flags=16384) at ../net/socket.c:2031
#15 0xffffffff8176f2e2 in SYSC_sendmsg (flags=<optimised out>, msg=<optimised out>, fd=<optimised out>) at ../net/socket.c:2042
#16 SyS_sendmsg (fd=<optimised out>, msg=<optimised out>, flags=<optimised out>) at ../net/socket.c:2038
#17 0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```