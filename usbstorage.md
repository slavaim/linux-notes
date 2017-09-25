
```
#0  storage_probe (intf=0xffff880406d9f000, id=0xffffffffc05e0420 <usb_storage_usb_ids+10176>) at ../drivers/usb/storage/usb.c:1104
#1  0xffffffff81627507 in usb_probe_interface (dev=0xffff880406d9f030) at ../drivers/usb/core/driver.c:361
#2  0xffffffff8155e728 in really_probe (drv=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:385
#3  driver_probe_device (drv=0xffffffffc05db1c8 <usb_storage_driver+104>, dev=0xffff880406d9f030) at ../drivers/base/dd.c:529
#4  0xffffffff8155ea6e in __device_attach_driver (drv=0xffffffffc05db1c8 <usb_storage_driver+104>, _data=0xffffc90001b4fa18) at ../drivers/base/dd.c:625
#5  0xffffffff8155c4e8 in bus_for_each_drv (bus=<optimised out>, start=<optimised out>, data=0x80 <irq_stack_union+128>, fn=0x0 <irq_stack_union>) at ../drivers/base/bus.c:463
#6  0xffffffff8155e30b in __device_attach (dev=0xffff880406d9f030, allow_async=true) at ../drivers/base/dd.c:682
#7  0xffffffff8155eae3 in device_initial_probe (dev=<optimised out>) at ../drivers/base/dd.c:729
#8  0xffffffff8155d722 in bus_probe_device (dev=0xffff880406d9f030) at ../drivers/base/bus.c:557
#9  0xffffffff8155b541 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1706
#10 0xffffffff8162549c in usb_set_configuration (dev=<optimised out>, configuration=1) at ../drivers/usb/core/message.c:1932
#11 0xffffffff8163032e in generic_probe (udev=0xffff880406d9f000) at ../drivers/usb/core/generic.c:174
#12 0xffffffff8162736e in usb_probe_device (dev=<optimised out>) at ../drivers/usb/core/driver.c:266
#13 0xffffffff8155e728 in really_probe (drv=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:385
#14 driver_probe_device (drv=0xffffffff81f05568 <usb_generic_driver+40>, dev=0xffff88040a36c098) at ../drivers/base/dd.c:529
#15 0xffffffff8155ea6e in __device_attach_driver (drv=0xffffffff81f05568 <usb_generic_driver+40>, _data=0xffffc90001b4fc70) at ../drivers/base/dd.c:625
#16 0xffffffff8155c4e8 in bus_for_each_drv (bus=<optimised out>, start=<optimised out>, data=0x80 <irq_stack_union+128>, fn=0x0 <irq_stack_union>) at ../drivers/base/bus.c:463
#17 0xffffffff8155e30b in __device_attach (dev=0xffff88040a36c098, allow_async=true) at ../drivers/base/dd.c:682
#18 0xffffffff8155eae3 in device_initial_probe (dev=<optimised out>) at ../drivers/base/dd.c:729
#19 0xffffffff8155d722 in bus_probe_device (dev=0xffff88040a36c098) at ../drivers/base/bus.c:557
#20 0xffffffff8155b541 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1706
#21 0xffffffff8161a9e4 in usb_new_device (udev=0xffff88040a36c000) at ../drivers/usb/core/hub.c:2453
#22 0xffffffff8161c8fe in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4894
#23 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#24 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#25 hub_event (work=0xffff88040b1a9dd0) at ../drivers/usb/core/hub.c:5185
#26 0xffffffff81094648 in process_one_work ()
#27 0xffffffff81094c7d in worker_thread ()
#28 0xffffffff8109a329 in kthread ()
#29 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
```

```
#0  hub_port_logical_disconnect (hub=0xffff88040b1a9c00, port1=6) at ../drivers/usb/core/hub.c:919
#1  0xffffffff81618e0d in usb_reset_and_verify_device (udev=0xffff88040b1a9c00) at ../drivers/usb/core/hub.c:5565
#2  0xffffffff8161945b in usb_reset_device (udev=0xffff8804081d8000) at ../drivers/usb/core/hub.c:5648
#3  0xffffffffc05d603d in usb_stor_port_reset (us=0xffff880405d8f7c0) at ../drivers/usb/storage/transport.c:1436
#4  0xffffffffc05d60e1 in usb_stor_invoke_transport (srb=0xffff880408267548, us=0xffff880405d8f7c0) at ../drivers/usb/storage/transport.c:911
#5  0xffffffffc05d4dae in usb_stor_transparent_scsi_command (srb=<optimised out>, us=<optimised out>) at ../drivers/usb/storage/protocol.c:124
#6  0xffffffffc05d75f8 in usb_stor_control_thread (__us=0xffff880405d8f7c0) at ../drivers/usb/storage/usb.c:394
#7  0xffffffff8109a329 in kthread ()
#8  0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#9  0x0000000000000000 in ?? ()
```

```
#0  usb_stor_disconnect (intf=0xffff88040a21b400) at ../drivers/usb/storage/usb.c:1091
#1  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff88040a21b430) at ../drivers/usb/core/driver.c:423
#2  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#3  device_release_driver_internal (dev=0xffff88040a21b430, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#4  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#5  0xffffffff8155d82d in bus_remove_device (dev=0xffff88040a21b400) at ../drivers/base/bus.c:600
#6  0xffffffff81559ed4 in device_del (dev=0xffff88040a21b430) at ../drivers/base/core.c:1856
#7  0xffffffff816246de in usb_disable_device (dev=0xffff88040a21b400, skip_ep0=10384784) at ../drivers/usb/core/message.c:1170
#8  0xffffffff8161a104 in usb_disconnect (pdev=0xffff88040b1b5800) at ../drivers/usb/core/hub.c:2120
#9  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#10 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#11 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#12 hub_event (work=0xffff88040b1a9dd0) at ../drivers/usb/core/hub.c:5185
#13 0xffffffff81094648 in process_one_work ()
#14 0xffffffff81094c7d in worker_thread ()
#15 0xffffffff8109a329 in kthread ()
#16 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
```

```
Thread 91 hit Breakpoint 1, device_del (dev=0xffff8804068fb810) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8804068fb810) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8804068fb810) at ../drivers/base/core.c:1891
#2  0xffffffff8162b74f in usb_remove_ep_devs (endpoint=0xffff88040592ab40) at ../drivers/usb/core/endpoint.c:215
#3  0xffffffff81623b4d in remove_intf_ep_devs (intf=0xffff8804068fb810) at ../drivers/usb/core/message.c:1045
#4  0xffffffff816246d5 in usb_disable_device (dev=0xffff8804068fb810, skip_ep0=1) at ../drivers/usb/core/message.c:1169
#5  0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#6  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#7  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#8  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#9  hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#10 0xffffffff81094648 in process_one_work (worker=0xffff8804068fb810, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#11 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#12 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#13 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#14 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8804068fcc10) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8804068fcc10) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8804068fcc10) at ../drivers/base/core.c:1891
#2  0xffffffff8162b74f in usb_remove_ep_devs (endpoint=0xffff88040592ab90) at ../drivers/usb/core/endpoint.c:215
#3  0xffffffff81623b4d in remove_intf_ep_devs (intf=0xffff8804068fcc10) at ../drivers/usb/core/message.c:1045
#4  0xffffffff816246d5 in usb_disable_device (dev=0xffff8804068fcc10, skip_ep0=270652544) at ../drivers/usb/core/message.c:1169
#5  0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#6  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#7  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#8  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#9  hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#10 0xffffffff81094648 in process_one_work (worker=0xffff8804068fcc10, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#11 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#12 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#13 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#14 0x0000000000000000 in ?? ()
Thread 91 hit Breakpoint 1, device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1820
#1  0xffffffff816246de in usb_disable_device (dev=0xffff8804068fc030, skip_ep0=270652544) at ../drivers/usb/core/message.c:1170
#2  0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#3  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#4  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#5  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#6  hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#7  0xffffffff81094648 in process_one_work (worker=0xffff8804068fc030, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#8  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#9  0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#10 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#11 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e7113c00) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e7113c00) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8803e7113c00) at ../drivers/base/core.c:1891
#2  0xffffffff813c64c8 in bsg_unregister_queue (q=<optimised out>) at ../block/bsg.c:964
#3  0xffffffff815ba0ca in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1288
#4  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#5  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#6  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#7  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#8  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#9  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#10 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#11 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#12 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7113c00) at ../drivers/base/bus.c:600
#13 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#14 0xffffffff816246de in usb_disable_device (dev=0xffff8803e7113c00, skip_ep0=212425) at ../drivers/usb/core/message.c:1170
#15 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#16 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#17 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#18 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#19 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#20 0xffffffff81094648 in process_one_work (worker=0xffff8803e7113c00, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#21 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#22 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#23 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#24 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e88fdc68) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e88fdc68) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8803e88fdc68) at ../drivers/base/core.c:1891
#2  0xffffffff815ba0d6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1289
#3  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#4  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#5  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#6  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#7  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#8  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#9  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#10 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#11 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e88fdc68) at ../drivers/base/bus.c:600
#12 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#13 0xffffffff816246de in usb_disable_device (dev=0xffff8803e88fdc68, skip_ep0=-393225776) at ../drivers/usb/core/message.c:1170
#14 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#15 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#16 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#17 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#18 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#19 0xffffffff81094648 in process_one_work (worker=0xffff8803e88fdc68, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#20 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#21 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#22 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#23 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e7113400) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e7113400) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8803e7113400) at ../drivers/base/core.c:1891
#2  0xffffffff8155a0fc in device_destroy (class=<optimised out>, devt=22020099) at ../drivers/base/core.c:2449
#3  0xffffffff815c9a5f in sg_remove_device (cl_dev=<optimised out>, cl_intf=<optimised out>) at ../drivers/scsi/sg.c:1610
#4  0xffffffff81559e6e in device_del (dev=0xffff8803e88fdc68) at ../drivers/base/core.c:1849
#5  0xffffffff8155a03a in device_unregister (dev=0xffff8803e7113400) at ../drivers/base/core.c:1891
#6  0xffffffff815ba0d6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1289
#7  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#8  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#9  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#10 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#11 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#12 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#13 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#14 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#15 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7113400) at ../drivers/base/bus.c:600
#16 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#17 0xffffffff816246de in usb_disable_device (dev=0xffff8803e7113400, skip_ep0=-418302904) at ../drivers/usb/core/message.c:1170
#18 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#19 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#20 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#21 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#22 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#23 0xffffffff81094648 in process_one_work (worker=0xffff8803e7113400, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#24 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#25 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#26 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#27 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 3716]
[New Thread 3717]

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1820
#1  0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1292
#2  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#3  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#4  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#5  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#6  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#7  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#8  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#9  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#10 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e88fd988) at ../drivers/base/bus.c:600
#11 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#12 0xffffffff816246de in usb_disable_device (dev=0xffff8803e88fd988, skip_ep0=-393225848) at ../drivers/usb/core/message.c:1170
#13 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#14 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#15 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#16 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#17 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#18 0xffffffff81094648 in process_one_work (worker=0xffff8803e88fd988, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#19 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#20 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#21 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#22 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e7116010) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e7116010) at ../drivers/base/core.c:1820
#1  0xffffffff815c3c25 in sd_remove (dev=0xffff8803e88fd988) at ../drivers/scsi/sd.c:3373
#2  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#3  device_release_driver_internal (dev=0xffff8803e88fd988, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#4  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#5  0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7116010) at ../drivers/base/bus.c:600
#6  0xffffffff81559ed4 in device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1856
#7  0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1292
#8  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#9  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#10 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#11 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#12 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#13 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#14 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#15 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#16 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7116010) at ../drivers/base/bus.c:600
#17 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#18 0xffffffff816246de in usb_disable_device (dev=0xffff8803e7116010, skip_ep0=582) at ../drivers/usb/core/message.c:1170
#19 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#20 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#21 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#22 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#23 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#24 0xffffffff81094648 in process_one_work (worker=0xffff8803e7116010, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#25 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#26 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#27 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#28 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e7117028) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e7117028) at ../drivers/base/core.c:1820
#1  0xffffffff813bb5bb in delete_partition (disk=<optimised out>, partno=<optimised out>) at ../block/partition-generic.c:267
#2  0xffffffff813ba8eb in del_gendisk (disk=0xffff8803e88ff000) at ../block/genhd.c:654
#3  0xffffffff815c3c31 in sd_remove (dev=0xffff8803e88fd988) at ../drivers/scsi/sd.c:3374
#4  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#5  device_release_driver_internal (dev=0xffff8803e88fd988, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#6  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#7  0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7117028) at ../drivers/base/bus.c:600
#8  0xffffffff81559ed4 in device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1856
#9  0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1292
#10 0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#11 0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#12 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#13 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#14 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#15 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#16 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#17 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#18 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e7117028) at ../drivers/base/bus.c:600
#19 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#20 0xffffffff816246de in usb_disable_device (dev=0xffff8803e7117028, skip_ep0=270690496) at ../drivers/usb/core/message.c:1170
#21 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#22 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#23 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#24 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#25 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#26 0xffffffff81094648 in process_one_work (worker=0xffff8803e7117028, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#27 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#28 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#29 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#30 0x0000000000000000 in ?? ()
(gdb) c
Thread 91 hit Breakpoint 1, device_del (dev=0xffff8804060dc400) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8804060dc400) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8804060dc400) at ../drivers/base/core.c:1891
#2  0xffffffff811acfef in bdi_unregister (bdi=0xffff88040a35a400) at ../mm/backing-dev.c:933
#3  0xffffffff813ba96b in del_gendisk (disk=0xffff8803e88ff000) at ../block/genhd.c:669
#4  0xffffffff815c3c31 in sd_remove (dev=0xffff8803e88fd988) at ../drivers/scsi/sd.c:3374
#5  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#6  device_release_driver_internal (dev=0xffff8803e88fd988, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#7  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#8  0xffffffff8155d82d in bus_remove_device (dev=0xffff8804060dc400) at ../drivers/base/bus.c:600
#9  0xffffffff81559ed4 in device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1856
#10 0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1292
#11 0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#12 0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#13 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#14 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#15 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#16 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#17 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#18 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#19 0xffffffff8155d82d in bus_remove_device (dev=0xffff8804060dc400) at ../drivers/base/bus.c:600
#20 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#21 0xffffffff816246de in usb_disable_device (dev=0xffff8804060dc400, skip_ep0=185276736) at ../drivers/usb/core/message.c:1170
#22 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#23 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#24 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#25 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#26 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#27 0xffffffff81094648 in process_one_work (worker=0xffff8804060dc400, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#28 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#29 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#30 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#31 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
Thread 91 hit Breakpoint 1, device_del (dev=0xffff8803e88ff070) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8803e88ff070) at ../drivers/base/core.c:1820
#1  0xffffffff813baaa3 in del_gendisk (disk=<optimised out>) at ../block/genhd.c:684
#2  0xffffffff815c3c31 in sd_remove (dev=0xffff8803e88fd988) at ../drivers/scsi/sd.c:3374
#3  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#4  device_release_driver_internal (dev=0xffff8803e88fd988, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#5  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#6  0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e88ff070) at ../drivers/base/bus.c:600
#7  0xffffffff81559ed4 in device_del (dev=0xffff8803e88fd988) at ../drivers/base/core.c:1856
#8  0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88fd800) at ../drivers/scsi/scsi_sysfs.c:1292
#9  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#10 0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#11 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#12 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#13 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#14 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#15 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#16 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#17 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e88ff070) at ../drivers/base/bus.c:600
#18 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#19 0xffffffff816246de in usb_disable_device (dev=0xffff8803e88ff070, skip_ep0=185953728) at ../drivers/usb/core/message.c:1170
#20 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#21 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#22 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#23 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#24 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#25 0xffffffff81094648 in process_one_work (worker=0xffff8803e88ff070, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#26 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#27 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#28 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#29 0x0000000000000000 in ?? ()
(gdb) c
Thread 91 hit Breakpoint 2, attribute_container_remove_device (dev=0xffff8803e88fd988, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
warning: Source file is more recent than executable.
211	{
(gdb) bt
#0  attribute_container_remove_device (dev=0xffff8803e88fd988, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
#1  0xffffffff81563705 in transport_destroy_device (dev=<optimised out>) at ../drivers/base/transport_class.c:278
#2  0xffffffff815ba096 in __scsi_remove_device (sdev=0xffff8803e88fd988) at ../drivers/scsi/scsi_sysfs.c:1307
#3  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#4  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#5  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#6  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#7  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#8  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#9  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#10 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#11 0xffffffff8155d82d in bus_remove_device (dev=0xffff8803e88fd988) at ../drivers/base/bus.c:600
#12 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#13 0xffffffff816246de in usb_disable_device (dev=0xffff8803e88fd988, skip_ep0=-2125056240) at ../drivers/usb/core/message.c:1170
#14 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#15 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#16 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#17 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#18 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#19 0xffffffff81094648 in process_one_work (worker=0xffff8803e88fd988, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#20 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#21 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#22 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#23 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff88040a359828) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff88040a359828) at ../drivers/base/core.c:1820
#1  0xffffffff815b6131 in scsi_target_reap_ref_release (kref=<optimised out>) at ../drivers/scsi/scsi_scan.c:394
#2  0xffffffff815b773e in kref_put (release=<optimised out>, kref=<optimised out>) at ../include/linux/kref.h:70
#3  scsi_target_reap_ref_put (starget=<optimised out>) at ../drivers/scsi/scsi_scan.c:401
#4  scsi_target_reap (starget=<optimised out>) at ../drivers/scsi/scsi_scan.c:521
#5  0xffffffff815ba0a6 in __scsi_remove_device (sdev=0xffff88040a359828) at ../drivers/scsi/scsi_sysfs.c:1314
#6  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#7  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#8  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#9  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#10 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#11 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#12 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#13 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#14 0xffffffff8155d82d in bus_remove_device (dev=0xffff88040a359828) at ../drivers/base/bus.c:600
#15 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#16 0xffffffff816246de in usb_disable_device (dev=0xffff88040a359828, skip_ep0=171284520) at ../drivers/usb/core/message.c:1170
#17 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#18 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#19 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#20 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#21 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#22 0xffffffff81094648 in process_one_work (worker=0xffff88040a359828, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#23 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#24 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#25 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#26 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 3776]

Thread 91 hit Breakpoint 2, attribute_container_remove_device (dev=0xffff88040a359828, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
211	{
(gdb) bt
#0  attribute_container_remove_device (dev=0xffff88040a359828, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
#1  0xffffffff81563705 in transport_destroy_device (dev=<optimised out>) at ../drivers/base/transport_class.c:278
#2  0xffffffff815b607b in scsi_target_destroy (starget=0xffff88040a359800) at ../drivers/scsi/scsi_scan.c:322
#3  0xffffffff815b6139 in scsi_target_reap_ref_release (kref=<optimised out>) at ../drivers/scsi/scsi_scan.c:396
#4  0xffffffff815b773e in kref_put (release=<optimised out>, kref=<optimised out>) at ../include/linux/kref.h:70
#5  scsi_target_reap_ref_put (starget=<optimised out>) at ../drivers/scsi/scsi_scan.c:401
#6  scsi_target_reap (starget=<optimised out>) at ../drivers/scsi/scsi_scan.c:521
#7  0xffffffff815ba0a6 in __scsi_remove_device (sdev=0xffff88040a359828) at ../drivers/scsi/scsi_sysfs.c:1314
#8  0xffffffff815b8650 in scsi_forget_host (shost=0xffff880406d96000) at ../drivers/scsi/scsi_scan.c:1891
#9  0xffffffff815ac157 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:173
#10 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#11 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#12 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#13 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#14 device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#15 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#16 0xffffffff8155d82d in bus_remove_device (dev=0xffff88040a359828) at ../drivers/base/bus.c:600
#17 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#18 0xffffffff816246de in usb_disable_device (dev=0xffff88040a359828, skip_ep0=-2125056240) at ../drivers/usb/core/message.c:1170
#19 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#20 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#21 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#22 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#23 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#24 0xffffffff81094648 in process_one_work (worker=0xffff88040a359828, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#25 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#26 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#27 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#28 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 2, attribute_container_remove_device (dev=0xffff880406d961e0, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
211	{
(gdb) bt
#0  attribute_container_remove_device (dev=0xffff880406d961e0, fn=0xffffffff81563710 <transport_destroy_classdev>) at ../drivers/base/attribute_container.c:211
#1  0xffffffff81563705 in transport_destroy_device (dev=<optimised out>) at ../drivers/base/transport_class.c:278
#2  0xffffffff815ac1a7 in transport_unregister_device (dev=<optimised out>) at ../include/linux/transport_class.h:82
#3  scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:182
#4  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#5  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#6  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#7  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#8  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#9  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#10 0xffffffff8155d82d in bus_remove_device (dev=0xffff880406d961e0) at ../drivers/base/bus.c:600
#11 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#12 0xffffffff816246de in usb_disable_device (dev=0xffff880406d961e0, skip_ep0=-2125056240) at ../drivers/usb/core/message.c:1170
#13 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#14 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#15 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#16 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#17 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#18 0xffffffff81094648 in process_one_work (worker=0xffff880406d961e0, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#19 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#20 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#21 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#22 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff880406d964c0) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff880406d964c0) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff880406d964c0) at ../drivers/base/core.c:1891
#2  0xffffffff815ac1b3 in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:183
#3  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#4  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#5  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#6  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#7  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#8  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#9  0xffffffff8155d82d in bus_remove_device (dev=0xffff880406d964c0) at ../drivers/base/bus.c:600
#10 0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#11 0xffffffff816246de in usb_disable_device (dev=0xffff880406d964c0, skip_ep0=114909664) at ../drivers/usb/core/message.c:1170
#12 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#13 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#14 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#15 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#16 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#17 0xffffffff81094648 in process_one_work (worker=0xffff880406d964c0, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#18 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#19 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#20 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#21 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff880406d961e0) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff880406d961e0) at ../drivers/base/core.c:1820
#1  0xffffffff815ac1bb in scsi_remove_host (shost=0xffff880406d96000) at ../drivers/scsi/hosts.c:184
#2  0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#3  usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#4  0xffffffff81626d52 in usb_unbind_interface (dev=0xffff8804068fc030) at ../drivers/usb/core/driver.c:423
#5  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#6  device_release_driver_internal (dev=0xffff8804068fc030, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#7  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#8  0xffffffff8155d82d in bus_remove_device (dev=0xffff880406d961e0) at ../drivers/base/bus.c:600
#9  0xffffffff81559ed4 in device_del (dev=0xffff8804068fc030) at ../drivers/base/core.c:1856
#10 0xffffffff816246de in usb_disable_device (dev=0xffff880406d961e0, skip_ep0=271051840) at ../drivers/usb/core/message.c:1170
#11 0xffffffff8161a104 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2120
#12 0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#13 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#14 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#15 hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#16 0xffffffff81094648 in process_one_work (worker=0xffff880406d961e0, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#17 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#18 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#19 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#20 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Thread 91 hit Breakpoint 1, device_del (dev=0xffff8804068fc410) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff8804068fc410) at ../drivers/base/core.c:1820
#1  0xffffffff8155a03a in device_unregister (dev=0xffff8804068fc410) at ../drivers/base/core.c:1891
#2  0xffffffff8162b74f in usb_remove_ep_devs (endpoint=0xffff880406c4f048) at ../drivers/usb/core/endpoint.c:215
#3  0xffffffff8161a19f in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2139
#4  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#5  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#6  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#7  hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#8  0xffffffff81094648 in process_one_work (worker=0xffff8804068fc410, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#9  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#10 0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#11 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#12 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
[New Thread 3778]
[New Thread 3777]

Thread 91 hit Breakpoint 1, device_del (dev=0xffff880406c4f098) at ../drivers/base/core.c:1820
1820	{
(gdb) bt
#0  device_del (dev=0xffff880406c4f098) at ../drivers/base/core.c:1820
#1  0xffffffff8161a1b0 in usb_disconnect (pdev=0xffff8803e871e800) at ../drivers/usb/core/hub.c:2146
#2  0xffffffff8161c218 in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4745
#3  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#4  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#5  hub_event (work=0xffff8803e86e4fd0) at ../drivers/usb/core/hub.c:5185
#6  0xffffffff81094648 in process_one_work (worker=0xffff880406c4f098, work=0xffff8803e86e4fd0) at ../kernel/workqueue.c:2097
#7  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b576000) at ../kernel/workqueue.c:2231
#8  0xffffffff8109a329 in kthread (_create=0xffff88040b590040) at ../kernel/kthread.c:231
#9  0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#10 0x0000000000000000 in ?? ()
(gdb) c
Continuing.
```
