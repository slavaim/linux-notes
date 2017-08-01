
```
#0  __switch_to (prev_p=0xffffffff81e104c0 <init_task>, next_p=0xffff88001d664f80) at ../arch/x86/kernel/process_64.c:273
#1  0xffffffff818a55cf in context_switch (rf=<optimised out>, next=<optimised out>, prev=<optimised out>, rq=<optimised out>) at ../kernel/sched/core.c:2879
#2  __schedule (preempt=<optimised out>) at ../kernel/sched/core.c:3440
#3  0xffffffff818a5ae6 in schedule () at ../kernel/sched/core.c:3499
#4  0xffffffff8109c429 in worker_thread (__worker=0xffff88001d467540) at ../kernel/workqueue.c:2252
#5  0xffffffff810a2659 in kthread (_create=0xffff88001d436b80) at ../kernel/kthread.c:231
#6  0xffffffff818ab0f5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#7  0x0000000000000000 in ?? ()
```
