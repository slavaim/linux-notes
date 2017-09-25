
USB core creates an attribut "remove" in sysfs as an interface for safe remove command.

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
