
## Matching

At first the general ```usb_device_type``` for a whole device is matched to the ```usb_generic_driver``` driver
```
struct usb_device_driver usb_generic_driver = {
	.name =	"usb",
	.probe = generic_probe,
	.disconnect = generic_disconnect,
#ifdef	CONFIG_PM
	.suspend = generic_suspend,
	.resume = generic_resume,
#endif
	.supports_autosuspend = 1,
};
```
```
#0  usb_probe_device (dev=0xffff8803e8991098) at ../drivers/usb/core/driver.c:250
#1  0xffffffff8155e728 in really_probe (drv=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:385
#2  driver_probe_device (drv=0xffffffff81f05568 <usb_generic_driver+40>, dev=0xffff8803e8991098) at ../drivers/base/dd.c:529
#3  0xffffffff8155ea6e in __device_attach_driver (drv=0xffffffff81f05568 <usb_generic_driver+40>, _data=0xffffc90001bbfc70) at ../drivers/base/dd.c:625
#4  0xffffffff8155c4e8 in bus_for_each_drv (bus=<optimised out>, start=<optimised out>, data=0xffff8803e8ad6850, fn=0xffff8803e89910b0) at ../drivers/base/bus.c:463
#5  0xffffffff8155e30b in __device_attach (dev=0xffff8803e8991098, allow_async=true) at ../drivers/base/dd.c:682
#6  0xffffffff8155eae3 in device_initial_probe (dev=<optimised out>) at ../drivers/base/dd.c:729
#7  0xffffffff8155d722 in bus_probe_device (dev=0xffff8803e8991098) at ../drivers/base/bus.c:557
#8  0xffffffff8155b541 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1706
#9  0xffffffff8161a9e4 in usb_new_device (udev=0xffff8803e8991000) at ../drivers/usb/core/hub.c:2453
#10 0xffffffff8161c8fe in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4894
#11 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#12 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#13 hub_event (work=0xffff8803e80a7bd0) at ../drivers/usb/core/hub.c:5185
#14 0xffffffff81094648 in process_one_work (worker=0xffff8803e8991098, work=0xffff8803e80a7bd0) at ../kernel/workqueue.c:2097
#15 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b5ad000) at ../kernel/workqueue.c:2231
#16 0xffffffff8109a329 in kthread (_create=0xffff88040b5af040) at ../kernel/kthread.c:231
#17 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
(gdb) p/x dev->type
$10 = 0xffffffff81f041c0
(gdb) p/x usb_device_type
$11 = {name = 0xffffffff81cc79c3, groups = 0x0, uevent = 0xffffffff816156d0, devnode = 0xffffffff816156a0, release = 0xffffffff81615630, pm = 0xffffffff81ab6760}
(gdb) p/x &((struct usb_device_driver*)(0))->drvwrap.driver
$19 = 0x28
(gdb) p ((struct usb_device_driver*)(0xffffffff81f05568-0x28))->name
$22 = 0xffffffff81caca8b "usb"
(gdb) p/x *((struct usb_device_driver*)(0xffffffff81f05568-0x28))
$25 = {
  name = 0xffffffff81caca8b, 
  probe = 0xffffffff81630300, 
  disconnect = 0xffffffff816300b0, 
  suspend = 0xffffffff81630070, 
  resume = 0xffffffff81630040, 
  drvwrap = {
    driver = {
      name = 0xffffffff81caca8b, 
      bus = 0xffffffff81f04500, 
      owner = 0x0, 
      mod_name = 0x0, 
      suppress_bind_attrs = 0x0, 
      probe_type = 0x0, 
      of_match_table = 0x0, 
      acpi_match_table = 0x0, 
      probe = 0xffffffff81627340, 
      remove = 0xffffffff816264d0, 
      shutdown = 0x0, 
      suspend = 0x0, 
      resume = 0x0, 
      groups = 0x0, 
      pm = 0x0, 
      p = 0xffff88040b194cc0
    }, 
    for_devices = 0x1
  }, 
  supports_autosuspend = 0x1
}
(gdb) x/i 0xffffffff81630300
   0xffffffff81630300 <generic_probe>:	nopl   0x0(%rax,%rax,1)
(gdb) x/i 0xffffffff816264d0
   0xffffffff816264d0 <usb_unbind_device>:	nopl   0x0(%rax,%rax,1)
```

Then each interface is matched to a corresponding driver ( the debug session below is not connected with the one for usb_generic_driver which you can see above, the device had been replugged ).

```
(gdb) bt
#0  usb_probe_interface (dev=0xffff88040543e830) at ../drivers/usb/core/driver.c:284
#1  0xffffffff8155e728 in really_probe (drv=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:385
#2  driver_probe_device (drv=0xffffffffc00561c8 <usb_storage_driver+104>, dev=0xffff88040543e830) at ../drivers/base/dd.c:529
#3  0xffffffff8155ea6e in __device_attach_driver (drv=0xffffffffc00561c8 <usb_storage_driver+104>, _data=0xffffc90001bbfa18) at ../drivers/base/dd.c:625
#4  0xffffffff8155c4e8 in bus_for_each_drv (bus=<optimised out>, start=<optimised out>, data=0xffff8803e89978b0, fn=0xffff88040543e848) at ../drivers/base/bus.c:463
#5  0xffffffff8155e30b in __device_attach (dev=0xffff88040543e830, allow_async=true) at ../drivers/base/dd.c:682
#6  0xffffffff8155eae3 in device_initial_probe (dev=<optimised out>) at ../drivers/base/dd.c:729
#7  0xffffffff8155d722 in bus_probe_device (dev=0xffff88040543e830) at ../drivers/base/bus.c:557
#8  0xffffffff8155b541 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1706
#9  0xffffffff8162549c in usb_set_configuration (dev=<optimised out>, configuration=1) at ../drivers/usb/core/message.c:1932
#10 0xffffffff8163032e in generic_probe (udev=0xffff88040543e830) at ../drivers/usb/core/generic.c:174
#11 0xffffffff8162736e in usb_probe_device (dev=<optimised out>) at ../drivers/usb/core/driver.c:266
#12 0xffffffff8155e728 in really_probe (drv=<optimised out>, dev=<optimised out>) at ../drivers/base/dd.c:385
#13 driver_probe_device (drv=0xffffffff81f05568 <usb_generic_driver+40>, dev=0xffff8803e8997898) at ../drivers/base/dd.c:529
#14 0xffffffff8155ea6e in __device_attach_driver (drv=0xffffffff81f05568 <usb_generic_driver+40>, _data=0xffffc90001bbfc70) at ../drivers/base/dd.c:625
#15 0xffffffff8155c4e8 in bus_for_each_drv (bus=<optimised out>, start=<optimised out>, data=0xffff8803e89978b0, fn=0xffff88040543e848) at ../drivers/base/bus.c:463
#16 0xffffffff8155e30b in __device_attach (dev=0xffff8803e8997898, allow_async=true) at ../drivers/base/dd.c:682
#17 0xffffffff8155eae3 in device_initial_probe (dev=<optimised out>) at ../drivers/base/dd.c:729
#18 0xffffffff8155d722 in bus_probe_device (dev=0xffff8803e8997898) at ../drivers/base/bus.c:557
#19 0xffffffff8155b541 in device_add (dev=<optimised out>) at ../drivers/base/core.c:1706
#20 0xffffffff8161a9e4 in usb_new_device (udev=0xffff8803e8997800) at ../drivers/usb/core/hub.c:2453
#21 0xffffffff8161c8fe in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4894
#22 hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#23 port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#24 hub_event (work=0xffff8803e80a7bd0) at ../drivers/usb/core/hub.c:5185
#25 0xffffffff81094648 in process_one_work (worker=0xffff88040543e830, work=0xffff8803e80a7bd0) at ../kernel/workqueue.c:2097
#26 0xffffffff81094c7d in worker_thread (__worker=0xffff88040b5ad000) at ../kernel/workqueue.c:2231
#27 0xffffffff8109a329 in kthread (_create=0xffff88040b5af040) at ../kernel/kthread.c:231
#28 0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424
#29 0x0000000000000000 in ?? ()
(gdb) p/x dev
(gdb) x/i 0xffffffffc00521d0
   0xffffffffc00521d0 <storage_probe>:	nopl   0x0(%rax,%rax,1)
(gdb) p/x dev->type
$36 = 0xffffffff81f044c0
(gdb) info symbol 0xffffffff81f044c0
usb_if_device_type in section .data of /work/linux/linux-4.12.4/build/vmlinux
$26 = 0xffff88040543e830
(gdb) p/x dev->driver
$27 = 0xffffffffc00561c8
(gdb) ptype dev->driver
type = struct device_driver {
    const char *name;
    struct bus_type *bus;
    struct module *owner;
    const char *mod_name;
    bool suppress_bind_attrs;
    enum probe_type probe_type;
    const struct of_device_id *of_match_table;
    const struct acpi_device_id *acpi_match_table;
    int (*probe)(struct device *);
    int (*remove)(struct device *);
    void (*shutdown)(struct device *);
    int (*suspend)(struct device *, pm_message_t);
    int (*resume)(struct device *);
    const struct attribute_group **groups;
    const struct dev_pm_ops *pm;
    struct driver_private *p;
} *
(gdb) p/x *dev->driver
$38 = {
  name = 0xffffffffc00537a0, 
  bus = 0xffffffff81f04500, 
  owner = 0xffffffffc005b6c0, 
  mod_name = 0xffffffffc00537d8, 
  suppress_bind_attrs = 0x0, 
  probe_type = 0x0, 
  of_match_table = 0x0, 
  acpi_match_table = 0x0, 
  probe = 0xffffffff816273b0, 
  remove = 0xffffffff81626ce0, 
  shutdown = 0x0, 
  suspend = 0x0, 
  resume = 0x0, 
  groups = 0x0, 
  pm = 0x0, 
  p = 0xffff8803e81d0780
}
(gdb) info symbol 0xffffffff816273b0
usb_probe_interface in section .text of /work/linux/linux-4.12.4/build/vmlinux
(gdb) ptype struct usb_driver
type = struct usb_driver {
    const char *name;
    int (*probe)(struct usb_interface *, const struct usb_device_id *);
    void (*disconnect)(struct usb_interface *);
    int (*unlocked_ioctl)(struct usb_interface *, unsigned int, void *);
    int (*suspend)(struct usb_interface *, pm_message_t);
    int (*resume)(struct usb_interface *);
    int (*reset_resume)(struct usb_interface *);
    int (*pre_reset)(struct usb_interface *);
    int (*post_reset)(struct usb_interface *);
    const struct usb_device_id *id_table;
    struct usb_dynids dynids;
    struct usbdrv_wrap drvwrap;
    unsigned int no_dynamic_id : 1;
    unsigned int supports_autosuspend : 1;
    unsigned int disable_hub_initiated_lpm : 1;
    unsigned int soft_unbind : 1;
}
(gdb) p/x &(((struct usb_driver*)(0))->drvwrap.driver)
$32 = 0x68
(gdb) p ((struct usb_driver*)(0xffffffffc00561c8-0x68))
$33 = (struct usb_driver *) 0xffffffffc0056160 <usb_storage_driver>
(gdb) p ((struct usb_driver*)(0xffffffffc00561c8-0x68))->name
$34 = 0xffffffffc00537a0 "usb-storage"
(gdb) p/x *((struct usb_driver*)(0xffffffffc00561c8-0x68))
$35 = {
  name = 0xffffffffc00537a0, 
  probe = 0xffffffffc00521d0, 
  disconnect = 0xffffffffc00523c0, 
  unlocked_ioctl = 0x0, 
  suspend = 0xffffffffc0051560, 
  resume = 0xffffffffc00515a0, 
  reset_resume = 0xffffffffc00515e0, 
  pre_reset = 0xffffffffc0051540, 
  post_reset = 0xffffffffc0051600, 
  id_table = 0xffffffffc0058c60, 
  dynids = {
    lock = {
      {
        rlock = {
          raw_lock = {
            val = {
              counter = 0x0
            }
          }
        }
      }
    }, 
    list = {
      next = 0xffffffffc00561b8, 
      prev = 0xffffffffc00561b8
    }
  }, 
  drvwrap = {
    driver = {
      name = 0xffffffffc00537a0, 
      bus = 0xffffffff81f04500, 
      owner = 0xffffffffc005b6c0, 
      mod_name = 0xffffffffc00537d8, 
      suppress_bind_attrs = 0x0, 
      probe_type = 0x0, 
      of_match_table = 0x0, 
      acpi_match_table = 0x0, 
      probe = 0xffffffff816273b0, 
      remove = 0xffffffff81626ce0, 
      shutdown = 0x0, 
      suspend = 0x0, 
      resume = 0x0, 
      groups = 0x0, 
      pm = 0x0, 
      p = 0xffff8803e81d0780
    }, 
    for_devices = 0x0
  }, 
  no_dynamic_id = 0x0, 
  supports_autosuspend = 0x1, 
  disable_hub_initiated_lpm = 0x0, 
  soft_unbind = 0x1
}
(gdb) x/i 0xffffffffc00521d0
   0xffffffffc00521d0 <storage_probe>:	nopl   0x0(%rax,%rax,1)
```


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

A usb_device is allocated by a call to ```usb_alloc_dev``` :

```
#0  usb_alloc_dev (parent=0xffff8803e8218800, bus=0xffff88040b60b000, port1=6) at ../drivers/usb/core/usb.c:556
#1  0xffffffff8161c44a in hub_port_connect (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4800
#2  hub_port_connect_change (portchange=<optimised out>, portstatus=<optimised out>, port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:4999
#3  port_event (port1=<optimised out>, hub=<optimised out>) at ../drivers/usb/core/hub.c:5105
#4  hub_event (work=0xffff8803e80a7bd0) at ../drivers/usb/core/hub.c:5185
#5  0xffffffff81094648 in process_one_work (worker=0xffff8803e8218800, work=0xffff8803e80a7bd0) at ../kernel/workqueue.c:2097
#6  0xffffffff81094c7d in worker_thread (__worker=0xffff88040b5ad000) at ../kernel/workqueue.c:2231
#7  0xffffffff8109a329 in kthread (_create=0xffff88040b5af040) at ../kernel/kthread.c:231
#8  0xffffffff818283b5 in ret_from_fork () at ../arch/x86/entry/entry_64.S:424

```

Let's set a watchpoint for the ```usb_device->dev.kobj.parent``` field to detect inserting the allocated usb_device in the usb devices hierarchy:

```
(gdb) p/x &((struct usb_device*)0xffff8803e8994000)->dev.kobj.parent
$6 = 0xffff8803e89940c0
(gdb) p ((struct usb_device*)0xffff8803e8994000)->dev.kobj.name
$7 = 0xffff880406c19990 "2-1.6"
(gdb) watch *0xffff8803e89940c0
Hardware watchpoint 3: *0xffff8803e89940c0
```

When the allocated usb_device is being inserted in the hierarchy the system stops on the watchpoint:

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
