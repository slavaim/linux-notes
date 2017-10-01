Adding a USB pen drive:

```
Thread 146 hit Breakpoint 4, devtmpfs_create_node (dev=0xffff88040a04b400) at ../drivers/base/devtmpfs.c:83
83	{
(gdb) bt
#0  devtmpfs_create_node (dev=0xffff88040a04b400) at ../drivers/base/devtmpfs.c:83
#1  0xffffffff81568d27 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1695
#2  0xffffffff81568f38 in device_create_groups_vargs (class=<optimised out>, parent=0xffff88040abfb988, devt=22020101, drvdata=<optimised out>, groups=<optimised out>, fmt=<optimised out>, 
    args=0xffffc900022cfcc8) at ../drivers/base/core.c:2301
#3  0xffffffff81568fc1 in device_create_vargs (args=<optimised out>, fmt=<optimised out>, drvdata=<optimised out>, devt=<optimised out>, parent=<optimised out>, class=<optimised out>)
    at ../drivers/base/core.c:2341
#4  device_create (class=<optimised out>, parent=<optimised out>, devt=<optimised out>, drvdata=<optimised out>, fmt=<optimised out>) at ../drivers/base/core.c:2377
#5  0xffffffff815d9385 in sg_add_device (cl_dev=<optimised out>, cl_intf=<optimised out>) at ../drivers/scsi/sg.c:1523
#6  0xffffffff81568bf4 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1721
#7  0xffffffff815c74a7 in scsi_sysfs_add_sdev (sdev=0xffff88040a04b400) at ../drivers/scsi/scsi_sysfs.c:1239
#8  0xffffffff815c5b1e in scsi_sysfs_add_devices (shost=<optimised out>) at ../drivers/scsi/scsi_scan.c:1720
#9  scsi_finish_async_scan (data=<optimised out>) at ../drivers/scsi/scsi_scan.c:1804
#10 do_scan_async (_data=0xffff88040869ed40, c=<optimised out>) at ../drivers/scsi/scsi_scan.c:1847
#11 0xffffffff8109d6b7 in async_run_entry_fn (work=0xffff88040a04b400) at ../kernel/async.c:123
#12 0xffffffff81094648 in process_one_work (worker=0xffff88040a04b400, work=0xffff88040976c440) at ../kernel/workqueue.c:2097
#13 0xffffffff81094c7d in worker_thread (__worker=0xffff8803e873d000) at ../kernel/workqueue.c:2231
#14 0xffffffff8109a329 in kthread (_create=0xffff88040090f440) at ../kernel/kthread.c:231
#15 0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#16 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 71]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8803e8f5ad78 "sg5", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8803e8f5ad78 "sg5", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 155]

Thread 146 hit Breakpoint 4, devtmpfs_create_node (dev=0xffff8803e7231000) at ../drivers/base/devtmpfs.c:83
83	{
(gdb) bt
#0  devtmpfs_create_node (dev=0xffff8803e7231000) at ../drivers/base/devtmpfs.c:83
#1  0xffffffff81568d27 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1695
#2  0xffffffff81568f38 in device_create_groups_vargs (class=<optimised out>, parent=0xffff88040abfb988, devt=261095429, drvdata=<optimised out>, groups=<optimised out>, fmt=<optimised out>, 
    args=0xffffc900022cfd40) at ../drivers/base/core.c:2301
#3  0xffffffff81568fc1 in device_create_vargs (args=<optimised out>, fmt=<optimised out>, drvdata=<optimised out>, devt=<optimised out>, parent=<optimised out>, class=<optimised out>)
    at ../drivers/base/core.c:2341
#4  device_create (class=<optimised out>, parent=<optimised out>, devt=<optimised out>, drvdata=<optimised out>, fmt=<optimised out>) at ../drivers/base/core.c:2377
#5  0xffffffff813d3389 in bsg_register_queue (q=0xffff8803e7231000, parent=0xffff8803e58acd98, name=0xffff8803e82a3b00 "", release=0x0 <irq_stack_union>) at ../block/bsg.c:1011
#6  0xffffffff815c74d0 in scsi_sysfs_add_sdev (sdev=0xffff8803e7231000) at ../drivers/scsi/scsi_sysfs.c:1250
#7  0xffffffff815c5b1e in scsi_sysfs_add_devices (shost=<optimised out>) at ../drivers/scsi/scsi_scan.c:1720
#8  scsi_finish_async_scan (data=<optimised out>) at ../drivers/scsi/scsi_scan.c:1804
#9  do_scan_async (_data=0xffff88040869ed40, c=<optimised out>) at ../drivers/scsi/scsi_scan.c:1847
#10 0xffffffff8109d6b7 in async_run_entry_fn (work=0xffff8803e7231000) at ../kernel/async.c:123
#11 0xffffffff81094648 in process_one_work (worker=0xffff8803e7231000, work=0xffff88040976c440) at ../kernel/workqueue.c:2097
#12 0xffffffff81094c7d in worker_thread (__worker=0xffff8803e873d000) at ../kernel/workqueue.c:2231
#13 0xffffffff8109a329 in kthread (_create=0xffff88040090f440) at ../kernel/kthread.c:231
#14 0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#15 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 71]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff880405d2ae50 "bsg/5:0:0:0", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff880405d2ae50 "bsg/5:0:0:0", mode=8576, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 3010]
[New Thread 3011]
[New Thread 3012]
[Switching to Thread 95]

Thread 103 hit Breakpoint 4, devtmpfs_create_node (dev=0xffff8803e7b60070) at ../drivers/base/devtmpfs.c:83
83	{
(gdb) bt
#0  devtmpfs_create_node (dev=0xffff8803e7b60070) at ../drivers/base/devtmpfs.c:83
#1  0xffffffff81568d27 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1695
#2  0xffffffff813c77b8 in register_disk (disk=<optimised out>, parent=<optimised out>) at ../block/genhd.c:525
#3  device_add_disk (parent=<optimised out>, disk=0xffff8803e7b60000) at ../block/genhd.c:622
#4  0xffffffff815d4080 in sd_probe_async (data=0xffff88040a04e400, cookie=<optimised out>) at ../drivers/scsi/sd.c:3224
#5  0xffffffff8109d6b7 in async_run_entry_fn (work=0xffff8803e7b60070) at ../kernel/async.c:123
#6  0xffffffff81094648 in process_one_work (worker=0xffff8803e7b60070, work=0xffff88040a0fdf80) at ../kernel/workqueue.c:2097
#7  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b7a5840) at ../kernel/workqueue.c:2231
#8  0xffffffff8109a329 in kthread (_create=0xffff88040bbc5900) at ../kernel/kthread.c:231
#9  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#10 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 71]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8804086bcb50 "sdd", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8804086bcb50 "sdd", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 95]

Thread 103 hit Breakpoint 4, devtmpfs_create_node (dev=0xffff88040088c028) at ../drivers/base/devtmpfs.c:83
83	{
(gdb) bt
#0  devtmpfs_create_node (dev=0xffff88040088c028) at ../drivers/base/devtmpfs.c:83
#1  0xffffffff81568d27 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1695
#2  0xffffffff813c8f59 in add_partition (disk=0xffff8803e7b60000, partno=<optimised out>, start=<optimised out>, len=<optimised out>, flags=<optimised out>, info=0xffffc90002311095)
    at ../block/partition-generic.c:349
#3  0xffffffff813c936b in rescan_partitions (disk=0xffff8803e7b60000, bdev=0xffff8803e6c38340) at ../block/partition-generic.c:597
#4  0xffffffff81261e6c in __blkdev_get (bdev=0xffff8803e6c38340, mode=1, for_part=<optimised out>) at ../fs/block_dev.c:1487
#5  0xffffffff81262135 in blkdev_get (bdev=0xffff8803e6c38340, mode=<optimised out>, holder=0xffff8803e7b60080) at ../fs/block_dev.c:1595
#6  0xffffffff813c798b in register_disk (disk=<optimised out>, parent=<optimised out>) at ../block/genhd.c:559
#7  device_add_disk (parent=<optimised out>, disk=0xffff8803e7b60000) at ../block/genhd.c:622
#8  0xffffffff815d4080 in sd_probe_async (data=0xffff88040a04e400, cookie=<optimised out>) at ../drivers/scsi/sd.c:3224
#9  0xffffffff8109d6b7 in async_run_entry_fn (work=0xffff88040088c028) at ../kernel/async.c:123
#10 0xffffffff81094648 in process_one_work (worker=0xffff88040088c028, work=0xffff88040a0fdf80) at ../kernel/workqueue.c:2097
#11 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b7a5840) at ../kernel/workqueue.c:2231
#12 0xffffffff8109a329 in kthread (_create=0xffff88040bbc5900) at ../kernel/kthread.c:231
#13 0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#14 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[Switching to Thread 71]

Thread 79 hit Breakpoint 2, handle_create (nodename=0xffff8804059e3f80 "sdd1", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
195	static int handle_create(const char *nodename, umode_t mode, kuid_t uid,
(gdb) bt
#0  handle_create (nodename=0xffff8804059e3f80 "sdd1", mode=24960, uid=..., gid=..., dev=<optimised out>) at ../drivers/base/devtmpfs.c:195
#1  0xffffffff81573598 in handle (dev=<optimised out>, gid=..., uid=..., mode=<optimised out>, name=<optimised out>) at ../drivers/base/devtmpfs.c:372
#2  devtmpfsd (p=<optimised out>) at ../drivers/base/devtmpfs.c:398
#3  0xffffffff8109a329 in kthread (_create=0xffff88040b5ef340) at ../kernel/kthread.c:231
#4  0xffffffff818355b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#5  0x0000000000000000 in ?? ()
(gdb) c
Continuing.
```
Adding and removing a USB pen drive:

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
