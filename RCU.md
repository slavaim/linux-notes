
```
#0  put_cred_rcu (rcu=0xffff88001d473ed8) at ../kernel/cred.c:148
#1  0xffffffff810b4b2a in __rcu_reclaim (head=<optimised out>, rn=<optimised out>) at ../kernel/rcu/rcu.h:195
#2  rcu_do_batch (rsp=<optimised out>, rsp=<optimised out>, rdp=<optimised out>) at ../kernel/rcu/tree.c:2800
#3  invoke_rcu_callbacks (rdp=<optimised out>, rsp=<optimised out>) at ../kernel/rcu/tree.c:3057
#4  __rcu_process_callbacks (rsp=<optimised out>) at ../kernel/rcu/tree.c:3024
#5  rcu_process_callbacks (unused=<optimised out>) at ../kernel/rcu/tree.c:3041
#6  0xffffffff810602d2 in __do_softirq () at ../kernel/softirq.c:284
#7  0xffffffff8106063b in invoke_softirq () at ../kernel/softirq.c:364
#8  irq_exit () at ../kernel/softirq.c:405
#9  0xffffffff8103e648 in exiting_irq () at ../arch/x86/include/asm/apic.h:652
#10 smp_apic_timer_interrupt (regs=<optimised out>) at ../arch/x86/kernel/apic/apic.c:966
#11 0xffffffff8193dc46 in apic_timer_interrupt () at ../arch/x86/entry/entry_64.S:701
```

```
#0  invoke_rcu_core () at ../kernel/rcu/tree.c:3065
#1  0xffffffff810b6a64 in rcu_check_callbacks (user=0) at ../kernel/rcu/tree.c:2885
#2  0xffffffff810bc7aa in update_process_times (user_tick=0) at ../kernel/time/timer.c:1571
#3  0xffffffff810cb0fd in tick_sched_handle (regs=<optimised out>, ts=<optimised out>, ts=<optimised out>) at ../kernel/time/tick-sched.c:155
#4  0xffffffff810cb638 in tick_sched_timer (timer=0xffff88001fc135c0) at ../kernel/time/tick-sched.c:1174
#5  0xffffffff810bd09c in __run_hrtimer (now=<optimised out>, timer=<optimised out>, base=<optimised out>, cpu_base=<optimised out>) at ../kernel/time/hrtimer.c:1212
#6  __hrtimer_run_queues (cpu_base=0xffff88001fc13180, now=<optimised out>) at ../kernel/time/hrtimer.c:1276
#7  0xffffffff810bd75c in hrtimer_interrupt (dev=<optimised out>) at ../kernel/time/hrtimer.c:1310
#8  0xffffffff8103de23 in local_apic_timer_interrupt () at ../arch/x86/kernel/apic/apic.c:941
#9  0xffffffff8103e643 in smp_apic_timer_interrupt (regs=<optimised out>) at ../arch/x86/kernel/apic/apic.c:965
#10 0xffffffff8193dc46 in apic_timer_interrupt () at ../arch/x86/entry/entry_64.S:701
```
