Reading osronline.com forums on Windows file system development I ran into a common misconception among Windows developers regarding UNIX design. http://osronline.com/cf.cfm?PageURL=showThread.CFM?link=285260

```
<QUOTE>
The essential difference between how the NT kernel works and how Unix was
designed is that NT caches streams of data (above the file system), whereas
on Unix data is cached at the block layer.
</QUOTE>
```

I spent 5 minutes to bust it.

This is true only for ancient *NIX kernels. Modern kernels use the same technique as NT with caching backed by file mapping structures. 

For example below is a call stack from my test machine running the Linux 4.12.2 kernel when ext4 read operation ext4_file_read_iter called the "Linux cache manager" ( do_generic_file_read -> page_cache_sync_readahead ) to bring data in the cache backed by mapped file structures( struct address_space ) when processing the read() system call. 

This resulted in a recursive call to mapping->a_ops->readpages into a file system's ext4_readpages . This is an analogue of a cached read in NT.  Mac OS X uses the same caching by file mapping technique borrowed from BSD.

```
(gdb) bt
#0  ext4_readpages (file=0xffff88001d59b300, mapping=0xffff88001d1d56c0, pages=0xffffc90000817c30, nr_pages=1) at ../fs/ext4/inode.c:3308
#1  0xffffffff811b6288 in read_pages (gfp=<optimised out>, nr_pages=<optimised out>, pages=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/readahead.c:121
#2  __do_page_cache_readahead (mapping=<optimised out>, filp=<optimised out>, offset=1, nr_to_read=<optimised out>, lookahead_size=<optimised out>) at ../mm/readahead.c:199
#3  0xffffffff811b64b8 in ra_submit (ra=<optimised out>, ra=<optimised out>, ra=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/internal.h:66
#4  ondemand_readahead (mapping=0xffff88001d1d56c0, ra=0xffff88001d59b398, filp=0xffff88001d59b300, hit_readahead_marker=<optimised out>, offset=0, req_size=<optimised out>) at ../mm/readahead.c:478
#5  0xffffffff811b678e in page_cache_sync_readahead (mapping=<optimised out>, ra=<optimised out>, filp=<optimised out>, offset=<optimised out>, req_size=<optimised out>) at ../mm/readahead.c:510
#6  0xffffffff811a7a62 in do_generic_file_read (written=<optimised out>, iter=<optimised out>, ppos=<optimised out>, filp=<optimised out>) at ../mm/filemap.c:1813
#7  generic_file_read_iter (iocb=0x20000, iter=<optimised out>) at ../mm/filemap.c:2069
#8  0xffffffff812d1386 in ext4_file_read_iter (iocb=0xffff88001d59b300, to=0xffff88001d1d56c0) at ../fs/ext4/file.c:70
#9  0xffffffff81237680 in call_read_iter (file=<optimised out>, iter=<optimised out>, kio=<optimised out>) at ../include/linux/fs.h:1728
#10 new_sync_read (ppos=<optimised out>, len=<optimised out>, buf=<optimised out>, filp=<optimised out>) at ../fs/read_write.c:440
#11 __vfs_read (file=0xffff88001d59b300, buf=<optimised out>, count=<optimised out>, pos=0xffffc90000817f18) at ../fs/read_write.c:452
#12 0xffffffff81237cc3 in vfs_read (file=0xffff88001d59b300, buf=0x7fb92a0cb000 <error: Cannot access memory at address 0x7fb92a0cb000>, count=<optimised out>, pos=0xffffc90000817f18)
    at ../fs/read_write.c:473
#13 0xffffffff81239385 in SYSC_read (count=<optimised out>, buf=<optimised out>, fd=<optimised out>) at ../fs/read_write.c:589
#14 SyS_read (fd=<optimised out>, buf=140433251151872, count=131072) at ../fs/read_write.c:582
#15 0xffffffff818aaffb in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203

```

```
(gdb) f 4
#4  ondemand_readahead (mapping=0xffff88001d1d56c0, ra=0xffff88001d59b398, filp=0xffff88001d59b300, hit_readahead_marker=<optimised out>, offset=0, req_size=<optimised out>) at ../mm/readahead.c:478
478		return ra_submit(ra, mapping, filp);

(gdb) p/x *mapping
$14 = {host = 0xffff88001d1d5548, page_tree = {gfp_mask = 0x1180020, rnode = 0x0}, tree_lock = {{rlock = {raw_lock = {val = {counter = 0x0}}}}}, i_mmap_writable = {counter = 0x0}, i_mmap = {
    rb_node = 0x0}, i_mmap_rwsem = {count = {counter = 0x0}, wait_list = {next = 0xffff88001d1d56f0, prev = 0xffff88001d1d56f0}, wait_lock = {raw_lock = {val = {counter = 0x0}}}, osq = {tail = {
        counter = 0x0}}, owner = 0x0}, nrpages = 0x0, nrexceptional = 0x0, writeback_index = 0x0, a_ops = 0xffffffff81a3a680, flags = 0x0, private_lock = {{rlock = {raw_lock = {val = {
            counter = 0x0}}}}}, gfp_mask = 0x14200ca, private_list = {next = 0xffff88001d1d5740, prev = 0xffff88001d1d5740}, private_data = 0x0}
            
(gdb) ptype mapping
type = struct address_space {
    struct inode *host;
    struct radix_tree_root page_tree;
    spinlock_t tree_lock;
    atomic_t i_mmap_writable;
    struct rb_root i_mmap;
    struct rw_semaphore i_mmap_rwsem;
    unsigned long nrpages;
    unsigned long nrexceptional;
    unsigned long writeback_index;
    const struct address_space_operations *a_ops;
    unsigned long flags;
    spinlock_t private_lock;
    gfp_t gfp_mask;
    struct list_head private_list;
    void *private_data;
} *

(gdb) f 1
#1  0xffffffff811b6288 in read_pages (gfp=<optimised out>, nr_pages=<optimised out>, pages=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/readahead.c:121
121			ret = mapping->a_ops->readpages(filp, mapping, pages, nr_pages);
(gdb) l
116		int ret;
117	
118		blk_start_plug(&plug);
119	
120		if (mapping->a_ops->readpages) {
121			ret = mapping->a_ops->readpages(filp, mapping, pages, nr_pages);
122			/* Clean up the remaining pages */
123			put_pages_list(pages);
124			goto out;
125		}

(gdb) f 9
#9  0xffffffff81237680 in call_read_iter (file=<optimised out>, iter=<optimised out>, kio=<optimised out>) at ../include/linux/fs.h:1728
1728		return file->f_op->read_iter(kio, iter);
(gdb) l
1723	} ____cacheline_aligned;
1724	
1725	static inline ssize_t call_read_iter(struct file *file, struct kiocb *kio,
1726					     struct iov_iter *iter)
1727	{
1728		return file->f_op->read_iter(kio, iter);
1729	}
1730	
1731	static inline ssize_t call_write_iter(struct file *file, struct kiocb *kio,
1732					      struct iov_iter *iter)
(gdb) 

```
