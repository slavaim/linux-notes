
```
#0  ext4_end_bio (bio=0xffff88001d1b0c00) at ../fs/ext4/page-io.c:297
#1  0xffffffff813dba31 in bio_endio (bio=0xffff88001d1b0c00) at ../block/bio.c:1833
#2  0xffffffff813e4238 in req_bio_endio (rq=<optimised out>, error=<optimised out>, nbytes=<optimised out>, bio=<optimised out>) at ../block/blk-core.c:145
#3  blk_update_request (req=0xffff88001d1b0c00, error=0, nr_bytes=49154) at ../block/blk-core.c:2631
#4  0xffffffff8160f463 in scsi_end_request (req=0xffff88001d379000, error=<optimised out>, bytes=<optimised out>, bidi_bytes=<optimised out>) at ../drivers/scsi/scsi_lib.c:645
#5  0xffffffff8161129f in scsi_io_completion (cmd=0xffff88001d379148, good_bytes=<optimised out>) at ../drivers/scsi/scsi_lib.c:862
#6  0xffffffff816082b9 in scsi_finish_command (cmd=0xffff88001d379148) at ../drivers/scsi/scsi.c:255
#7  0xffffffff816109c7 in scsi_softirq_done (rq=<optimised out>) at ../drivers/scsi/scsi_lib.c:1588
#8  0xffffffff813ecd8b in blk_done_softirq (h=<optimised out>) at ../block/blk-softirq.c:36
#9  0xffffffff818ae59d in __do_softirq () at ../kernel/softirq.c:284
#10 0xffffffff81088086 in invoke_softirq () at ../kernel/softirq.c:364
#11 irq_exit () at ../kernel/softirq.c:405
#12 0xffffffff818ad72f in exiting_irq () at ../arch/x86/include/asm/apic.h:652
#13 do_IRQ (regs=0xffffffff81e03d98 <init_thread_union+15768>) at ../arch/x86/kernel/irq.c:250
#14 0xffffffff818ab809 in common_interrupt () at ../arch/x86/entry/entry_64.S:512
#15 0xffffffff81e03d98 in init_thread_union ()
#16 0x0000000000000000 in ?? ()
```
