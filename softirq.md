
```
#0  __do_softirq () at ../kernel/softirq.c:242
#1  0xffffffff81088086 in invoke_softirq () at ../kernel/softirq.c:364
#2  irq_exit () at ../kernel/softirq.c:405
#3  0xffffffff818ae06d in exiting_irq () at ../arch/x86/include/asm/apic.h:652
#4  smp_apic_timer_interrupt (regs=<optimised out>) at ../arch/x86/kernel/apic/apic.c:966
#5  0xffffffff818acb09 in apic_timer_interrupt () at ../arch/x86/entry/entry_64.S:701
#6  0xffffffff81e03d48 in init_thread_union ()
```

```
#0  __do_softirq () at ../kernel/softirq.c:242
#1  0xffffffff81088086 in invoke_softirq () at ../kernel/softirq.c:364
#2  irq_exit () at ../kernel/softirq.c:405
#3  0xffffffff810add2f in scheduler_ipi () at ../kernel/sched/core.c:1793
#4  0xffffffff818add69 in __smp_reschedule_interrupt () at ../arch/x86/kernel/smp.c:262
#5  smp_reschedule_interrupt (regs=<optimised out>) at ../arch/x86/kernel/smp.c:268
#6  0xffffffff818ad2e9 in reschedule_interrupt () at ../arch/x86/entry/entry_64.S:724
```

```
#0  __do_softirq () at ../kernel/softirq.c:242
#1  0xffffffff81087f49 in run_ksoftirqd (cpu=<optimised out>) at ../kernel/softirq.c:676
#2  0xffffffff810a622a in smpboot_thread_fn (data=0x0 <irq_stack_union>) at ../kernel/smpboot.c:164
#3  0xffffffff810a2659 in kthread (_create=0xffff88001f132e40) at ../kernel/kthread.c:231
#4  0xffffffff818ab0f5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
```
