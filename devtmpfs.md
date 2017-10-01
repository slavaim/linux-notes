```
Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8803f46798c0 "bus/usb/002/005", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8803f46798c0 "bus/usb/002/005", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2623]
[New Thread 2624]
[New Thread 2625]
[New Thread 2626]
[New Thread 2627]
[New Thread 2628]
[New Thread 2638]
[New Thread 2674]
[New Thread 2675]
[New Thread 2676]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8803e8f5a7d0 "sg5", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8803e8f5a7d0 "sg5", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2677]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8803f4679930 "bsg/5:0:0:0", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8803f4679930 "bsg/5:0:0:0", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2678]
[New Thread 2681]
[New Thread 2682]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8803e8f5ab40 "sdd", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8803e8f5ab40 "sdd", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2683]
[New Thread 2685]
[New Thread 2686]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff88040a1fa9f0 "sdd1", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff88040a1fa9f0 "sdd1", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2988]
[New Thread 2984]
[New Thread 2927]
[New Thread 2930]
[New Thread 2931]
[New Thread 2932]
[New Thread 2975]
[New Thread 2982]
[New Thread 2983]

Thread 79 hit Breakpoint 3, handle_remove (nodename=0xffff8803e8eb9cc0 "bsg/5:0:0:0", dev=0xffff8803e8ed5000) at ../drivers/base/devtmpfs.c:299
299	{
(gdb) bt
#0  handle_remove (nodename=0xffff8803e8eb9cc0 "bsg/5:0:0:0", dev=0xffff8803e8ed5000) at ../drivers/base/devtmpfs.c:299
#1  0xffffffff8157355b in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:374
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 79 hit Breakpoint 3, handle_remove (nodename=0xffff8803e8f5a7d0 "sg5", dev=0xffff88040a04b400) at ../drivers/base/devtmpfs.c:299
299	{
(gdb) bt
#0  handle_remove (nodename=0xffff8803e8f5a7d0 "sg5", dev=0xffff88040a04b400) at ../drivers/base/devtmpfs.c:299
#1  0xffffffff8157355b in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:374
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2989]
[New Thread 2990]
[New Thread 2991]
[New Thread 2992]

Thread 79 hit Breakpoint 3, handle_remove (nodename=0xffff88040a1fa9f0 "sdd1", dev=0xffff8803e8ed0c28) at ../drivers/base/devtmpfs.c:299
299	{
(gdb) bt
#0  handle_remove (nodename=0xffff88040a1fa9f0 "sdd1", dev=0xffff8803e8ed0c28) at ../drivers/base/devtmpfs.c:299
#1  0xffffffff8157355b in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:374
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 79 hit Breakpoint 3, handle_remove (nodename=0xffff8803e8f5ab40 "sdd", dev=0xffff8803e7b62070) at ../drivers/base/devtmpfs.c:299
299	{
(gdb) bt
#0  handle_remove (nodename=0xffff8803e8f5ab40 "sdd", dev=0xffff8803e7b62070) at ../drivers/base/devtmpfs.c:299
#1  0xffffffff8157355b in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:374
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 2993]

Thread 79 hit Breakpoint 3, handle_remove (nodename=0xffff8803e8eb9cc0 "bus/usb/002/005", dev=0xffff8804082e3898) at ../drivers/base/devtmpfs.c:299
299	{
(gdb) bt
#0  handle_remove (nodename=0xffff8803e8eb9cc0 "bus/usb/002/005", dev=0xffff8804082e3898) at ../drivers/base/devtmpfs.c:299
#1  0xffffffff8157355b in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:374
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
```
