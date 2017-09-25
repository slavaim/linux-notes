```
#0  kgdb_breakpoint () at ../kernel/debug/debug_core.c:1073
#1  0xffffffff8112c3bc in sysrq_handle_dbg (key=<optimised out>) at ../kernel/debug/debug_core.c:826
#2  0xffffffff81502099 in __handle_sysrq (key=103, check_mask=true) at ../drivers/tty/sysrq.c:554
#3  0xffffffff8150248a in sysrq_handle_keypress (value=<optimised out>, code=<optimised out>, sysrq=<optimised out>) at ../drivers/tty/sysrq.c:816
#4  sysrq_filter (handle=<optimised out>, type=<optimised out>, code=<optimised out>, value=<optimised out>) at ../drivers/tty/sysrq.c:878
#5  0xffffffff8166a247 in input_to_handler (handle=0xffff8803e70af800, vals=0xffff8803e8310248, count=<optimised out>) at ../drivers/input/input.c:105
#6  0xffffffff8166b448 in input_pass_values (dev=0xffff880406164800, vals=0xffff8803e8310240, count=<optimised out>) at ../drivers/input/input.c:148
#7  0xffffffff8166cf90 in input_pass_values (count=<optimised out>, vals=<optimised out>, dev=<optimised out>) at ../drivers/input/input.c:400
#8  input_handle_event (dev=0xffff880406164800, type=0, code=0, value=0) at ../drivers/input/input.c:401
#9  0xffffffff8166d4a4 in input_event (dev=0x67 <irq_stack_union+103>, type=<optimised out>, code=<optimised out>, value=<optimised out>) at ../drivers/input/input.c:436
#10 0xffffffffc00199b8 in input_sync (dev=<optimised out>) at ../include/linux/input.h:414
#11 hidinput_report_event (hid=<optimised out>, report=<optimised out>) at ../drivers/hid/hid-input.c:1214
#12 0xffffffffc0017b38 in hid_report_raw_event (hid=0xffff8803f7bd31e0, type=<optimised out>, data=0xffff8803f7bd31e0 "\340\060\275\367\003\210\377\377", size=24, interrupt=<optimised out>)
    at ../drivers/hid/hid-core.c:1532
#13 0xffffffffc0017de2 in hid_input_report (hid=0x67 <irq_stack_union+103>, type=<optimised out>, data=0xffff88002d05d002 "\001\004F\n", size=8, interrupt=<optimised out>)
    at ../drivers/hid/hid-core.c:1592
#14 0xffffffffc007691f in logi_dj_recv_forward_report (dj_report=<optimised out>, djrcv_dev=<optimised out>) at ../drivers/hid/hid-logitech-dj.c:569
#15 logi_dj_dj_event (report=<optimised out>, size=<optimised out>, data=<optimised out>, hdev=<optimised out>) at ../drivers/hid/hid-logitech-dj.c:896
#16 logi_dj_raw_event (hdev=<optimised out>, report=<optimised out>, data=0xffff88002d05d000 " \002\001\004F\n", size=<optimised out>) at ../drivers/hid/hid-logitech-dj.c:972
#17 0xffffffffc0017e20 in hid_input_report (hid=0xffff88040b4b8000, type=<optimised out>, data=0xffff88002d05d000 " \002\001\004F\n", size=15, interrupt=<optimised out>) at ../drivers/hid/hid-core.c:1587
#18 0xffffffffc00cf102 in hid_irq_in (urb=0xffff8803e82519c0) at ../drivers/hid/usbhid/hid-core.c:285
#19 0xffffffff8161ecaa in __usb_hcd_giveback_urb (urb=0xffff8803e82519c0) at ../drivers/usb/core/hcd.c:1769
#20 0xffffffff8161fce2 in usb_giveback_urb_bh (param=<optimised out>) at ../drivers/usb/core/hcd.c:1796
#21 0xffffffff81080f18 in tasklet_hi_action (a=<optimised out>) at ../kernel/softirq.c:555
#22 0xffffffff8182ba49 in __do_softirq () at ../kernel/softirq.c:284
#23 0xffffffff81081427 in invoke_softirq () at ../kernel/softirq.c:364
#24 irq_exit () at ../kernel/softirq.c:405
#25 0xffffffff8182abd1 in exiting_irq () at ../arch/x86/include/asm/apic.h:652
#26 do_IRQ (regs=0xffffc90001947dc8) at ../arch/x86/kernel/irq.c:250
#27 0xffffffff81828ad3 in common_interrupt () at ../arch/x86/entry/entry_64.S:481
#28 0xffffc90001947dc8 in ?? ()
#29 0x0000000000000000 in ?? ()
```
