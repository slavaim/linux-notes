
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
