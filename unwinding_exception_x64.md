Generally GDB is unable to unwind a kernel call stack with an exception frame on it. The unwinding stops on an exception processing. For example

```
(gdb) bt
#0  delay_tsc (__loops=5241148) at ../arch/x86/lib/delay.c:78
#1  0xffffffff8134b532 in __delay (loops=<optimised out>) at ../arch/x86/lib/delay.c:160
#2  __const_udelay (xloops=<optimised out>) at ../arch/x86/lib/delay.c:174
#3  0xffffffff81132620 in panic (fmt=<optimised out>) at ../kernel/panic.c:297
#4  0xffffffff8101f080 in oops_end (flags=70, regs=0xffffc90000227c18, signr=9) at ../arch/x86/kernel/dumpstack.c:235
#5  0xffffffff8104d1c7 in no_context (regs=0xffffc90000227c18, error_code=0, address=8, signal=<optimised out>, si_code=<optimised out>) at ../arch/x86/mm/fault.c:867
#6  0xffffffff8104d456 in __bad_area_nosemaphore (regs=0xffffc90000227c18, error_code=0, address=8, vma=<optimised out>, si_code=196609) at ../arch/x86/mm/fault.c:953
#7  0xffffffff8104d59f in bad_area_nosemaphore (regs=<optimised out>, error_code=<optimised out>, address=<optimised out>, vma=<optimised out>) at ../arch/x86/mm/fault.c:960
#8  0xffffffff8104d8e7 in __do_page_fault (regs=0xffffc90000227c18, error_code=0, address=8) at ../arch/x86/mm/fault.c:1387
#9  0xffffffff8104dccc in do_page_fault (regs=<optimised out>, error_code=<optimised out>) at ../arch/x86/mm/fault.c:1508
#10 0xffffffff8193ecd2 in page_fault () at ../arch/x86/entry/entry_64.S:1005
#11 0xffff88001decdb40 in ?? ()
#12 0xffff88001c02ae48 in ?? ()
#13 0xffffc90000227d98 in ?? ()
#14 0xffff88001d733000 in ?? ()
#15 0xffffc90000227cf0 in ?? ()
#16 0xffff88001d733000 in ?? ()
#17 0xffff88001cd02510 in ?? ()
#18 0xffffc90000227e18 in ?? ()
#19 0x0000000000000000 in ?? ()
```

Linux has a structure ```struct pt_regs``` to save thread context state. A pointer to this strucrue is provided to an exception processing routine and contains a context of a thread when an exception happened. Using register values from this structure a call stack at the moment of exception can be captured with GDB.

```
(gdb) f 8
#8  0xffffffff8104d8e7 in __do_page_fault (regs=0xffffc90000227c18, error_code=0, address=8) at ../arch/x86/mm/fault.c:1387
1387				bad_area_nosemaphore(regs, error_code, address, NULL);
```

Having a valid regs pointer set register values.

```
(gdb) p/x *regs
$2 = {r15 = 0xffff88001decdb40, r14 = 0xffff88001c02ae48, r13 = 0xffffc90000227d98, r12 = 0xffff88001d733000, bp = 0xffffc90000227cf0, bx = 0xffff88001d733000, r11 = 0xffff88001cd02510, 
  r10 = 0xffffc90000227e18, r9 = 0x0, r8 = 0xffff88001fc9d180, ax = 0x0, cx = 0x0, dx = 0x1000, si = 0xffff88001d733000, di = 0xffffc90000227d00, orig_ax = 0xffffffffffffffff, ip = 0xffffffff811aa30c, 
  cs = 0x10, flags = 0x246, sp = 0xffffc90000227cc8, ss = 0x18}
(gdb) set $rip=regs->ip
(gdb) p/x $rip
$3 = 0xffffffff8134b5f4
(gdb) set $rsp=regs->sp
No symbol "regs" in current context.
(gdb) set $rbp=0xffffc90000227cf0
(gdb) set $rbx=0xffff88001d733000
```

Now a call  stack at the momemnt of exception can be examined.

```
(gdb) bt
#0  delay_tsc (__loops=5241148) at ../arch/x86/lib/delay.c:78
#1  0xffffffffc0000076 in redirfs_get_filename ()
#2  0xffffffffc0014121 in dummyflt_release (context=<optimised out>, args=0xffffc90000227d98) at /work/redirfs/src/dummyflt/dummyflt.c:104
#3  0xffffffffc000892e in rfs_precall_flts ()
#4  0xffffffffc0002a42 in rfs_release ()
#5  0xffffffff81193a7a in __fput (file=0xffff88001cd02500) at ../fs/file_table.c:209
#6  0xffffffff81193bb9 in ____fput (work=<optimised out>) at ../fs/file_table.c:245
#7  0xffffffff810758b9 in task_work_run () at ../kernel/task_work.c:116
#8  0xffffffff8105da35 in exit_task_work (task=<optimised out>) at ../include/linux/task_work.h:21
#9  do_exit (code=<optimised out>) at ../kernel/exit.c:878
#10 0xffffffff8105f14e in do_group_exit (exit_code=0) at ../kernel/exit.c:982
#11 0xffffffff8105f1bf in SYSC_exit_group (error_code=<optimised out>) at ../kernel/exit.c:993
#12 SyS_exit_group (error_code=<optimised out>) at ../kernel/exit.c:991
#13 0xffffffff8193d060 in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
#14 0x0000000000000000 in ?? ()
```
