
```
(gdb) bt
#0  ext4_drop_inode (inode=0xffff88001accaf50) at ../fs/ext4/super.c:994
#1  0xffffffff81257e9d in iput_final (inode=<optimised out>) at ../fs/inode.c:1489
#2  iput (inode=0xffff88001accaf50) at ../fs/inode.c:1540
#3  0xffffffff8124a2ef in do_unlinkat (dfd=-100, pathname=<optimised out>) at ../fs/namei.c:4050
#4  0xffffffff8124af8b in SYSC_unlinkat (flag=<optimised out>, pathname=<optimised out>, dfd=<optimised out>) at ../fs/namei.c:4086
#5  SyS_unlinkat (dfd=<optimised out>, pathname=<optimised out>, flag=<optimised out>) at ../fs/namei.c:4078
#6  0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
#7  0x0000000001d820f0 in ?? ()
#8  0x00007ffcfb903290 in ?? ()
#9  0x0000000000000000 in ?? ()
(gdb) b ext4_evict_inode
Breakpoint 39 at 0xffffffff812e4b70: file ../fs/ext4/inode.c, line 189.
(gdb) g
Ambiguous command "g": gcore, generate-core-file, goto-bookmark, gr, gu, guile, guile-repl.
(gdb) c
Continuing.

Thread 2 hit Breakpoint 39, ext4_evict_inode (inode=0xffff88001accaf50) at ../fs/ext4/inode.c:189
189	{
(gdb) bt
#0  ext4_evict_inode (inode=0xffff88001accaf50) at ../fs/ext4/inode.c:189
#1  0xffffffff81257c77 in evict (inode=0xffff88001accaf50) at ../fs/inode.c:552
#2  0xffffffff81257f6c in iput_final (inode=<optimised out>) at ../fs/inode.c:1513
#3  iput (inode=0xffff88001accaf50) at ../fs/inode.c:1540
#4  0xffffffff8124a2ef in do_unlinkat (dfd=-100, pathname=<optimised out>) at ../fs/namei.c:4050
#5  0xffffffff8124af8b in SYSC_unlinkat (flag=<optimised out>, pathname=<optimised out>, dfd=<optimised out>) at ../fs/namei.c:4086
#6  SyS_unlinkat (dfd=<optimised out>, pathname=<optimised out>, flag=<optimised out>) at ../fs/namei.c:4078
#7  0xffffffff818aae7b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
#8  0x0000000001d820f0 in ?? ()
#9  0x00007ffcfb903290 in ?? ()
#10 0x0000000000000000 in ?? ()

(gdb) f 2 
#2  0xffffffff81257f6c in iput_final (inode=<optimised out>) at ../fs/inode.c:1513

(gdb) l 1480,1520
1480	static void iput_final(struct inode *inode)
1481	{
1482		struct super_block *sb = inode->i_sb;
1483		const struct super_operations *op = inode->i_sb->s_op;
1484		int drop;
1485	
1486		WARN_ON(inode->i_state & I_NEW);
1487	
1488		if (op->drop_inode)
1489			drop = op->drop_inode(inode);
1490		else
1491			drop = generic_drop_inode(inode);
1492	
1493		if (!drop && (sb->s_flags & MS_ACTIVE)) {
1494			inode_add_lru(inode);
1495			spin_unlock(&inode->i_lock);
1496			return;
1497		}
1498	
1499		if (!drop) {
1500			inode->i_state |= I_WILL_FREE;
1501			spin_unlock(&inode->i_lock);
1502			write_inode_now(inode, 1);
1503			spin_lock(&inode->i_lock);
1504			WARN_ON(inode->i_state & I_NEW);
1505			inode->i_state &= ~I_WILL_FREE;
1506		}
1507	
1508		inode->i_state |= I_FREEING;
1509		if (!list_empty(&inode->i_lru))
1510			inode_lru_list_del(inode);
1511		spin_unlock(&inode->i_lock);
1512	
1513		evict(inode);
1514	}

```
