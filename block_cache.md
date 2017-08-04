
```
#0  ext4_get_block (inode=0xffff88001dae80e8, iblock=797, bh=0xffffc9000056bba8, create=0) at ../fs/ext4/inode.c:782
#1  0xffffffff8127231c in generic_block_bmap (mapping=<optimised out>, block=<optimised out>, get_block=<optimised out>) at ../fs/buffer.c:3029
#2  0xffffffff812dce3d in ext4_bmap (mapping=0xffff88001dae8260, block=797) at ../fs/ext4/inode.c:3270
#3  0xffffffff812567dc in bmap (inode=<optimised out>, block=<optimised out>) at ../fs/inode.c:1560
#4  0xffffffff81325d7b in jbd2_journal_bmap (journal=0xffff88001d4be800, blocknr=797, retp=0xffffc9000056bcb0) at ../fs/jbd2/journal.c:806
#5  0xffffffff81325e3b in jbd2_journal_next_log_block (journal=0xffff88001d4be800, retp=0xffffc9000056bcb0) at ../fs/jbd2/journal.c:789
#6  0xffffffff81325e88 in jbd2_journal_get_descriptor_buffer (transaction=0xffff88001cc40d00, type=1) at ../fs/jbd2/journal.c:841
#7  0xffffffff8131e9b0 in jbd2_journal_commit_transaction (journal=0xffff88001d4be800) at ../fs/jbd2/commit.c:603
#8  0xffffffff81323a32 in kjournald2 (arg=0xffff88001d4be800) at ../fs/jbd2/journal.c:233
#9  0xffffffff810a2659 in kthread (_create=0xffff88001d7832c0) at ../kernel/kthread.c:231
#10 0xffffffff818ab0f5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#11 0x0000000000000000 in ?? ()

(gdb) bt
#0  ext4_bmap (mapping=0xffff88001dae8260, block=823) at ../fs/ext4/inode.c:3219
#1  0xffffffff812567dc in bmap (inode=<optimised out>, block=<optimised out>) at ../fs/inode.c:1560
#2  0xffffffff81325d7b in jbd2_journal_bmap (journal=0xffff88001d4be800, blocknr=823, retp=0xffffc9000056bc48) at ../fs/jbd2/journal.c:806
#3  0xffffffff81325e3b in jbd2_journal_next_log_block (journal=0xffff88001d4be800, retp=0xffffc9000056bc48) at ../fs/jbd2/journal.c:789
#4  0xffffffff81325e88 in jbd2_journal_get_descriptor_buffer (transaction=0xffff88001cd39800, type=2) at ../fs/jbd2/journal.c:841
#5  0xffffffff8131dec2 in journal_submit_commit_record (journal=0xffff88001d4be800, commit_transaction=0xffff88001cd39800, cbh=0xffffc9000056bd70, crc32_sum=4294967295) at ../fs/jbd2/commit.c:134
#6  0xffffffff8131f258 in jbd2_journal_commit_transaction (journal=0xffff88001d4be800) at ../fs/jbd2/commit.c:870
#7  0xffffffff81323a32 in kjournald2 (arg=0xffff88001d4be800) at ../fs/jbd2/journal.c:233
#8  0xffffffff810a2659 in kthread (_create=0xffff88001d7832c0) at ../kernel/kthread.c:231
#9  0xffffffff818ab0f5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#10 0x0000000000000000 in ?? ()

(gdb) f 1
#1  0xffffffff812567dc in bmap (inode=<optimised out>, block=<optimised out>) at ../fs/inode.c:1560
1560			res = inode->i_mapping->a_ops->bmap(inode->i_mapping, block);
(gdb) l 1555,1565
1555	 */
1556	sector_t bmap(struct inode *inode, sector_t block)
1557	{
1558		sector_t res = 0;
1559		if (inode->i_mapping->a_ops->bmap)
1560			res = inode->i_mapping->a_ops->bmap(inode->i_mapping, block);
1561		return res;
1562	}
1563	EXPORT_SYMBOL(bmap);
1564	
1565	/*
(gdb) 
```
