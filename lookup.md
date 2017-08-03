
```
#0  ext4_lookup (dir=0xffff88001ce0f708, dentry=0xffff88001ace2a80, flags=0) at ../fs/ext4/namei.c:1537
#1  0xffffffff81245815 in lookup_slow (name=<optimised out>, dir=0xffff88001cd976c0, flags=0) at ../fs/namei.c:1655
#2  0xffffffff81245edf in walk_component (nd=0xffffc90000877cf0, flags=0) at ../fs/namei.c:1784
#3  0xffffffff81246736 in lookup_last (nd=<optimised out>) at ../fs/namei.c:2252
#4  path_lookupat (nd=0xffffc90000877cf0, flags=0, path=0xffffc90000877e50) at ../fs/namei.c:2302
#5  0xffffffff81249a28 in filename_lookup (dfd=<optimised out>, name=0xffff88001c629000, flags=0, path=0x0 <irq_stack_union>, root=<optimised out>) at ../fs/namei.c:2336
#6  0xffffffff81249be6 in user_path_at_empty (dfd=-100, name=<optimised out>, flags=0, path=0xffffc90000877e50, empty=<optimised out>) at ../fs/namei.c:2590
#7  0xffffffff8123dde7 in user_path_at (path=<optimised out>, flags=<optimised out>, name=<optimised out>, dfd=<optimised out>) at ../include/linux/namei.h:56
#8  vfs_statx (dfd=484505352, filename=0xffff88001ace2a80 "\200", flags=0, stat=<optimised out>, request_mask=<optimised out>) at ../fs/stat.c:184
#9  0xffffffff8123e3cd in vfs_lstat (stat=<optimised out>, name=<optimised out>) at ../include/linux/fs.h:2933
#10 SYSC_newlstat (filename=<optimised out>, statbuf=0x23f21b0) at ../fs/stat.c:349
#11 0xffffffff8123eb0e in SyS_newlstat (filename=<optimised out>, statbuf=<optimised out>) at ../fs/stat.c:343
#12 0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
#13 0x00007fc2ac5fb678 in ?? ()

(gdb) f 1
#1  0xffffffff81245815 in lookup_slow (name=<optimised out>, dir=0xffff88001cd976c0, flags=0) at ../fs/namei.c:1655
1655			old = inode->i_op->lookup(inode, dentry, flags);
(gdb) l
1650					dput(dentry);
1651					dentry = ERR_PTR(error);
1652				}
1653			}
1654		} else {
1655			old = inode->i_op->lookup(inode, dentry, flags);
1656			d_lookup_done(dentry);
1657			if (unlikely(old)) {
1658				dput(dentry);
1659				dentry = old;
(gdb) 
```
