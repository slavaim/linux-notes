
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
