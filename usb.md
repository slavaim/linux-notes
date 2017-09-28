
## Removal

USB core creates an attribute "remove" in sysfs as an interface for safe remove command.

```
/* "Safely remove a device" */
static ssize_t remove_store(struct device *dev, struct device_attribute *attr,
			    const char *buf, size_t count)
{
	struct usb_device *udev = to_usb_device(dev);
	int rc = 0;

	usb_lock_device(udev);
	if (udev->state != USB_STATE_NOTATTACHED) {

		/* To avoid races, first unconfigure and then remove */
		usb_set_configuration(udev, -1);
		rc = usb_remove_device(udev);
	}
	if (rc == 0)
		rc = count;
	usb_unlock_device(udev);
	return rc;
}
static DEVICE_ATTR_IGNORE_LOCKDEP(remove, S_IWUSR, NULL, remove_store);

static struct attribute *dev_attrs[] = {
	[...]
	&dev_attr_remove.attr,
	[...]
};
```

```
#0  device_del (dev=0xffff880408d66c28) at ../drivers/base/core.c:1820
#1  0xffffffff813bb5bb in delete_partition (disk=<optimised out>, partno=<optimised out>) at ../block/partition-generic.c:267
#2  0xffffffff813ba8eb in del_gendisk (disk=0xffff8803e88c5000) at ../block/genhd.c:654
#3  0xffffffff815c3c31 in sd_remove (dev=0xffff8803e88c1188) at ../drivers/scsi/sd.c:3374
#4  0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#5  device_release_driver_internal (dev=0xffff8803e88c1188, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#6  0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#7  0xffffffff8155d82d in bus_remove_device (dev=0xffff880408d66c28) at ../drivers/base/bus.c:600
#8  0xffffffff81559ed4 in device_del (dev=0xffff8803e88c1188) at ../drivers/base/core.c:1856
#9  0xffffffff815ba0e6 in __scsi_remove_device (sdev=0xffff8803e88c1000) at ../drivers/scsi/scsi_sysfs.c:1292
#10 0xffffffff815b8650 in scsi_forget_host (shost=0xffff8803e8851000) at ../drivers/scsi/scsi_scan.c:1891
#11 0xffffffff815ac157 in scsi_remove_host (shost=0xffff8803e8851000) at ../drivers/scsi/hosts.c:173
#12 0xffffffffc0880419 in quiesce_and_remove_host (us=<optimised out>) at ../drivers/usb/storage/usb.c:874
#13 usb_stor_disconnect (intf=<optimised out>) at ../drivers/usb/storage/usb.c:1094
#14 0xffffffff81626d52 in usb_unbind_interface (dev=0xffff880409009c30) at ../drivers/usb/core/driver.c:423
#15 0xffffffff8155ec31 in __device_release_driver (parent=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:833
#16 device_release_driver_internal (dev=0xffff880409009c30, drv=<optimised out>, parent=0x0 <irq_stack_union>) at ../drivers/base/dd.c:863
#17 0xffffffff8155ed02 in device_release_driver (dev=<optimised out>) at ../drivers/base/dd.c:888
#18 0xffffffff8155d82d in bus_remove_device (dev=0xffff880408d66c28) at ../drivers/base/bus.c:600
#19 0xffffffff81559ed4 in device_del (dev=0xffff880409009c30) at ../drivers/base/core.c:1856
#20 0xffffffff816246de in usb_disable_device (dev=0xffff880408d66c28, skip_ep0=270982592) at ../drivers/usb/core/message.c:1170
#21 0xffffffff816250d5 in usb_set_configuration (dev=0xffff880406c4b800, configuration=<optimised out>) at ../drivers/usb/core/message.c:1797
#22 0xffffffff8162a9d0 in remove_store (dev=<optimised out>, attr=<optimised out>, buf=<optimised out>, count=1) at ../drivers/usb/core/sysfs.c:763
#23 0xffffffff81558808 in dev_attr_store (kobj=<optimised out>, attr=<optimised out>, buf=<optimised out>, count=<optimised out>) at ../drivers/base/core.c:704
#24 0xffffffff8129432a in sysfs_kf_write (of=<optimised out>, buf=<optimised out>, count=<optimised out>, pos=<optimised out>) at ../fs/sysfs/file.c:141
#25 0xffffffff81293e0f in kernfs_fop_write (file=<optimised out>, user_buf=<optimised out>, count=1, ppos=0xffffc90003a0bf20) at ../fs/kernfs/file.c:316
#26 0xffffffff812145d8 in __vfs_write (file=0xffff88040951d000, p=<optimised out>, count=<optimised out>, pos=0x180400028) at ../fs/read_write.c:508
#27 0xffffffff812153e2 in vfs_write (file=0xffff880408d66c28, buf=0xffffea001026ddc0 "", count=1, pos=0xffffc90003a0bf20) at ../fs/read_write.c:558
#28 0xffffffff81216806 in SYSC_write (count=<optimised out>, buf=<optimised out>, fd=<optimised out>) at ../fs/read_write.c:605
#29 SyS_write (fd=<optimised out>, buf=140309974454272, count=1) at ../fs/read_write.c:597
#30 0xffffffff8182813b in entry_SYSCALL_64 () at ../arch/x86/entry/entry_64.S:203
```

## Allocation

A usb_device is allocated
```
0xffffffff8155b1e8 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1650
warning: Source file is more recent than executable.
1650			dev->kobj.parent = kobj;
(gdb) bt
#0  0xffffffff8155b1e8 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1650
#1  0xffffffff8161a9e4 in usb_new_device (udev=0xffff8803e8994000) at ../drivers/usb/core/hub.c:2453
#2  0xffffffff8161c8fe in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4894
#3  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#4  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#5  hub_event (work=0xffff8803e80a7bd0) at ../drivers/usb/core/hub.c:5185
#6  0xffffffff81094648 in process_one_work (worker=0xffff8803e8994098, work=0xffff8803e80a7bd0) at ../kernel/workqueue.c:2097
#7  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b5ad000) at ../kernel/workqueue.c:2231
#8  0xffffffff8109a329 in kthread (_create=0xffff88040b5af040) at ../kernel/kthread.c:231
#9  0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
```

A watchpoint is set for the ```usb_device->dev.kobj.parent``` field to detect inserting in the usb devices hierarchy:

```
(gdb) p/x &((struct usb_device*)0xffff8803e8994000)->dev.kobj.parent
$6 = 0xffff8803e89940c0
(gdb) p ((struct usb_device*)0xffff8803e8994000)->dev.kobj.name
$7 = 0xffff880406c19990 "2-1.6"
(gdb) watch *0xffff8803e89940c0
Hardware watchpoint 3: *0xffff8803e89940c0
```

The allocated usb_device is being inserted in the hierarchy. The system stops on the watchpoint:

```
Thread 93 received signal SIGTRAP, Trace/breakpoint trap.
[Switching to Thread 88]
0xffffffff8155b1e8 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1650
warning: Source file is more recent than executable.
1650			dev->kobj.parent = kobj;
(gdb) bt
#0  0xffffffff8155b1e8 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1650
#1  0xffffffff8161a9e4 in usb_new_device (udev=0xffff8803e8994000) at ../drivers/usb/core/hub.c:2453
#2  0xffffffff8161c8fe in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4894
#3  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#4  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#5  hub_event (work=0xffff8803e80a7bd0) at ../drivers/usb/core/hub.c:5185
#6  0xffffffff81094648 in process_one_work (worker=0xffff8803e8994098, work=0xffff8803e80a7bd0) at ../kernel/workqueue.c:2097
#7  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b5ad000) at ../kernel/workqueue.c:2231
#8  0xffffffff8109a329 in kthread (_create=0xffff88040b5af040) at ../kernel/kthread.c:231
#9  0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#10 0x0000000000000000 in ?? ()
(gdb) l
1645		pr_debug("device: '%s': %s\n", dev_name(dev), __func__);
1646	
1647		parent = get_device(dev->parent);
1648		kobj = get_device_parent(dev, parent);
1649		if (kobj)
1650			dev->kobj.parent = kobj;
1651	
1652		/* use parent numa_node */
1653		if (parent && (dev_to_node(dev) == NUMA_NO_NODE))
1654			set_dev_node(dev, dev_to_node(parent));
```
