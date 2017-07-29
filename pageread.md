
filemap ( cached read )

```
#0  ext4_readpages (file=0xffff88001dbe1100, mapping=0xffff88001d1d5288, pages=0xffffc900007ffb80, nr_pages=4) at ../fs/ext4/inode.c:3308
#1  0xffffffff811b6288 in read_pages (gfp=<optimised out>, nr_pages=<optimised out>, pages=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/readahead.c:121
#2  __do_page_cache_readahead (mapping=<optimised out>, filp=<optimised out>, offset=3, nr_to_read=<optimised out>, lookahead_size=<optimised out>) at ../mm/readahead.c:199
#3  0xffffffff811b64b8 in ra_submit (ra=<optimised out>, ra=<optimised out>, ra=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/internal.h:66
#4  ondemand_readahead (mapping=0xffff88001d1d5288, ra=0xffff88001dbe1198, filp=0xffff88001dbe1100, hit_readahead_marker=<optimised out>, offset=0, req_size=<optimised out>) at ../mm/readahead.c:478
#5  0xffffffff811b678e in page_cache_sync_readahead (mapping=<optimised out>, ra=<optimised out>, filp=<optimised out>, offset=<optimised out>, req_size=<optimised out>) at ../mm/readahead.c:510
#6  0xffffffff811a7a62 in do_generic_file_read (written=<optimised out>, iter=<optimised out>, ppos=<optimised out>, filp=<optimised out>) at ../mm/filemap.c:1813
#7  generic_file_read_iter (iocb=0x0 <irq_stack_union>, iter=<optimised out>) at ../mm/filemap.c:2069
#8  0xffffffff812d1386 in ext4_file_read_iter (iocb=0xffff88001dbe1100, to=0xffff88001d1d5288) at ../fs/ext4/file.c:70
#9  0xffffffff81237680 in call_read_iter (file=<optimised out>, iter=<optimised out>, kio=<optimised out>) at ../include/linux/fs.h:1728
#10 new_sync_read (ppos=<optimised out>, len=<optimised out>, buf=<optimised out>, filp=<optimised out>) at ../fs/read_write.c:440
#11 __vfs_read (file=0xffff88001dbe1100, buf=<optimised out>, count=<optimised out>, pos=0xffffc900007ffe58) at ../fs/read_write.c:452
#12 0xffffffff81237cc3 in vfs_read (file=0xffff88001dbe1100, buf=0xffff88001dbe1700 "", count=<optimised out>, pos=0xffffc900007ffe58) at ../fs/read_write.c:473
#13 0xffffffff8123f640 in kernel_read (count=<optimised out>, addr=<optimised out>, offset=<optimised out>, file=<optimised out>) at ../fs/exec.c:897
#14 prepare_binprm (bprm=0xffff88001dbe1700) at ../fs/exec.c:1553
#15 0xffffffff81240ca6 in do_execveat_common (fd=<optimised out>, filename=0xffff88001c56a000, flags=0, argv=..., envp=...) at ../fs/exec.c:1770
#16 0xffffffff812411c1 in do_execve (__envp=<optimised out>, __argv=<optimised out>, filename=<optimised out>) at ../fs/exec.c:1833
#17 SYSC_execve (envp=<optimised out>, argv=<optimised out>, filename=<optimised out>) at ../fs/exec.c:1914
#18 SyS_execve (filename=<optimised out>, argv=19915272, envp=19714568) at ../fs/exec.c:1909
#19 0xffffffff81003b5b in do_syscall_64 (regs=0xffff88001dbe1100) at ../arch/x86/entry/common.c:284
#20 0xffffffff818ab0ab in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:245
```

pagefault read

```
#0  ext4_readpages (file=0xffff88001dbe1100, mapping=0xffff88001d1d5288, pages=0xffffc900007ff9a0, nr_pages=17) at ../fs/ext4/inode.c:3308
#1  0xffffffff811b6288 in read_pages (gfp=<optimised out>, nr_pages=<optimised out>, pages=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/readahead.c:121
#2  __do_page_cache_readahead (mapping=<optimised out>, filp=<optimised out>, offset=23, nr_to_read=<optimised out>, lookahead_size=<optimised out>) at ../mm/readahead.c:199
#3  0xffffffff811a8529 in ra_submit (ra=<optimised out>, ra=<optimised out>, ra=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/internal.h:66
#4  do_sync_mmap_readahead (vma=<optimised out>, offset=<optimised out>, file=<optimised out>, ra=<optimised out>) at ../mm/filemap.c:2151
#5  filemap_fault (vmf=<optimised out>) at ../mm/filemap.c:2227
#6  0xffffffff812e7211 in ext4_filemap_fault (vmf=0xffffc900007ffb48) at ../fs/ext4/inode.c:5992
#7  0xffffffff811dc01e in __do_fault (vmf=0xffffc900007ffb48) at ../mm/memory.c:2973
#8  0xffffffff811dfd14 in do_cow_fault (vmf=<optimised out>) at ../mm/memory.c:3404
#9  do_fault (vmf=<optimised out>) at ../mm/memory.c:3477
#10 handle_pte_fault (vmf=<optimised out>) at ../mm/memory.c:3705
#11 __handle_mm_fault (vma=<optimised out>, address=<optimised out>, flags=21) at ../mm/memory.c:3823
#12 0xffffffff811e07b3 in handle_mm_fault (vma=0xffff88001d4e93c0, address=6382584, flags=21) at ../mm/memory.c:3860
#13 0xffffffff8106af10 in __do_page_fault (regs=0xffffc900007ffca8, error_code=2, address=6382584) at ../arch/x86/mm/fault.c:1445
#14 0xffffffff8106b1d2 in do_page_fault (regs=0xffffc900007ffca8, error_code=2) at ../arch/x86/mm/fault.c:1508
#15 0xffffffff818ac3e8 in page_fault () at ../arch/x86/entry/entry_64.S:1005
```

```
#0  ext4_readpages (file=0xffff88001dbe1100, mapping=0xffff88001d1d5288, pages=0xffffc900007ffbd0, nr_pages=2) at ../fs/ext4/inode.c:3308
#1  0xffffffff811b6288 in read_pages (gfp=<optimised out>, nr_pages=<optimised out>, pages=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/readahead.c:121
#2  __do_page_cache_readahead (mapping=<optimised out>, filp=<optimised out>, offset=23, nr_to_read=<optimised out>, lookahead_size=<optimised out>) at ../mm/readahead.c:199
#3  0xffffffff811b64b8 in ra_submit (ra=<optimised out>, ra=<optimised out>, ra=<optimised out>, filp=<optimised out>, mapping=<optimised out>) at ../mm/internal.h:66
#4  ondemand_readahead (mapping=0xffff88001d1d5288, ra=0xffff88001dbe1198, filp=0xffff88001dbe1100, hit_readahead_marker=<optimised out>, offset=1, req_size=<optimised out>) at ../mm/readahead.c:478
#5  0xffffffff811b664b in page_cache_async_readahead (mapping=0xffff88001d1d5288, ra=0xffff88001dbe1198, filp=0xffff88001dbe1100, page=<optimised out>, offset=1, req_size=32) at ../mm/readahead.c:554
#6  0xffffffff811a8411 in do_async_mmap_readahead (vma=<optimised out>, offset=<optimised out>, page=<optimised out>, file=<optimised out>, ra=<optimised out>) at ../mm/filemap.c:2172
#7  filemap_fault (vmf=<optimised out>) at ../mm/filemap.c:2224
#8  0xffffffff812e7211 in ext4_filemap_fault (vmf=0xffffc900007ffdf8) at ../fs/ext4/inode.c:5992
#9  0xffffffff811dc01e in __do_fault (vmf=0xffffc900007ffdf8) at ../mm/memory.c:2973
#10 0xffffffff811e0208 in do_read_fault (vmf=<optimised out>) at ../mm/memory.c:3375
#11 do_fault (vmf=<optimised out>) at ../mm/memory.c:3475
#12 handle_pte_fault (vmf=<optimised out>) at ../mm/memory.c:3705
#13 __handle_mm_fault (vma=<optimised out>, address=<optimised out>, flags=0) at ../mm/memory.c:3823
#14 0xffffffff811e07b3 in handle_mm_fault (vma=0xffff88001d4e9840, address=4198688, flags=84) at ../mm/memory.c:3860
#15 0xffffffff8106af10 in __do_page_fault (regs=0xffffc900007fff58, error_code=4, address=4198688) at ../arch/x86/mm/fault.c:1445
#16 0xffffffff8106b1d2 in do_page_fault (regs=0xffffc900007fff58, error_code=4) at ../arch/x86/mm/fault.c:1508
#17 0xffffffff818ac3e8 in page_fault () at ../arch/x86/entry/entry_64.S:1005
```

memory mapped file support

```
static const struct vm_operations_struct ext4_file_vm_ops = {
	.fault		= ext4_filemap_fault,
	.map_pages	= filemap_map_pages,
	.page_mkwrite   = ext4_page_mkwrite,
};

static int ext4_file_mmap(struct file *file, struct vm_area_struct *vma)
{
	struct inode *inode = file->f_mapping->host;

	if (unlikely(ext4_forced_shutdown(EXT4_SB(inode->i_sb))))
		return -EIO;

	if (ext4_encrypted_inode(inode)) {
		int err = fscrypt_get_encryption_info(inode);
		if (err)
			return 0;
		if (!fscrypt_has_encryption_key(inode))
			return -ENOKEY;
	}
	file_accessed(file);
	if (IS_DAX(file_inode(file))) {
		vma->vm_ops = &ext4_dax_vm_ops;
		vma->vm_flags |= VM_MIXEDMAP | VM_HUGEPAGE;
	} else {
		vma->vm_ops = &ext4_file_vm_ops;
	}
	return 0;
}

const struct file_operations ext4_file_operations = {
	.llseek		= ext4_llseek,
	.read_iter	= ext4_file_read_iter,
	.write_iter	= ext4_file_write_iter,
	.unlocked_ioctl = ext4_ioctl,
#ifdef CONFIG_COMPAT
	.compat_ioctl	= ext4_compat_ioctl,
#endif
	.mmap		= ext4_file_mmap,
	.open		= ext4_file_open,
	.release	= ext4_release_file,
	.fsync		= ext4_sync_file,
	.get_unmapped_area = thp_get_unmapped_area,
	.splice_read	= generic_file_splice_read,
	.splice_write	= iter_file_splice_write,
	.fallocate	= ext4_fallocate,
};
```
