
```
#0  native_safe_halt () at ../arch/x86/include/asm/irqflags.h:54
#1  0xffffffff818aa34e in arch_safe_halt () at ../arch/x86/include/asm/paravirt.h:98
#2  default_idle () at ../arch/x86/kernel/process.c:341
#3  0xffffffff81037d3f in arch_cpu_idle () at ../arch/x86/kernel/process.c:332
#4  0xffffffff818aa7e3 in default_idle_call () at ../kernel/sched/idle.c:98
#5  0xffffffff810c4efd in cpuidle_idle_call () at ../kernel/sched/idle.c:156
#6  do_idle () at ../kernel/sched/idle.c:245
#7  0xffffffff810c5161 in cpu_startup_entry (state=CPUHP_ONLINE) at ../kernel/sched/idle.c:350
#8  0xffffffff8189cdb7 in rest_init () at ../init/main.c:415
#9  0xffffffff81fae0b6 in start_kernel () at ../init/main.c:679
#10 0xffffffff81fad2e4 in x86_64_start_reservations (real_mode_data=<optimised out>) at ../arch/x86/kernel/head64.c:196
#11 0xffffffff81fad42f in x86_64_start_kernel (real_mode_data=0x14780 <tick_percpu_dev+448> <error: Cannot access memory at address 0x14780>) at ../arch/x86/kernel/head64.c:177
#12 0xffffffff810001bf in secondary_startup_64 () at ../arch/x86/kernel/head_64.S:304
```
