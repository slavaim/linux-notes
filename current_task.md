
The ```current``` task is saved in per-cpu space for x86-64 and is accessed through ```gs``` at ```current_task``` offset as

```
mov    %gs:0xd440,%rdx
```

```
(gdb) p/x __per_cpu_offset[0]
$61 = 0xffff88001fc00000
(gdb) p/x __per_cpu_offset
$62 = {0xffff88001fc00000, 0xffff88001fc80000, 0xffff88001fd00000, 0xffff88001fd80000, 0xffffffff81f8f000 <repeats 508 times>}
(gdb) p/x &current_task
$63 = 0xd440
(gdb) p/x __per_cpu_offset[0]
$64 = 0xffff88001fc00000
(gdb) x/gx 0xffff88001fc00000+0xd440
0xffff88001fc0d440:	0xffff88001dea6a00
(gdb) p/d ((struct task_struct*)0xffff88001dea6a00)->pid
$67 = 243
(gdb) p/x ((struct task_struct*)0xffff88001dea6a00)->mm
$69 = 0xffff88001d1bc800
(gdb) p/x ((struct task_struct*)0xffff88001dea6a00)->active_mm
$70 = 0xffff88001d1bc800
(gdb) p/x __per_cpu_offset[2]
$73 = 0xffff88001fd00000
(gdb) x/gx 0xffff88001fd00000+0xd440
0xffff88001fd0d440:	0xffff88001f240000
(gdb) p/x ((struct task_struct*)0xffff88001f240000)->pid
$74 = 0x1
(gdb) lx-ps
0xffffffff81e104c0 <init_task> 0 swapper/0
0xffff88001f240000 1 systemd
0xffff88001f240d40 2 kthreadd
0xffff88001f2427c0 4 kworker/0:0H
0xffff88001f244240 6 mm_percpu_wq
0xffff88001f244f80 7 ksoftirqd/0
0xffff88001f245cc0 8 rcu_sched
0xffff88001f246a00 9 rcu_bh
0xffff88001f298000 10 migration/0
0xffff88001f298d40 11 watchdog/0
0xffff88001f29c240 12 cpuhp/0
0xffff88001f29cf80 13 cpuhp/1
0xffff88001f29dcc0 14 watchdog/1
0xffff88001f29ea00 15 migration/1
0xffff88001f2c8000 16 ksoftirqd/1
0xffff88001f2c9a80 18 kworker/1:0H
0xffff88001f2ca7c0 19 cpuhp/2
0xffff88001f2cb500 20 watchdog/2
0xffff88001f2cc240 21 migration/2
0xffff88001f2ccf80 22 ksoftirqd/2
0xffff88001f2cea00 24 kworker/2:0H
0xffff88001f310000 25 cpuhp/3
0xffff88001f310d40 26 watchdog/3
0xffff88001f311a80 27 migration/3
0xffff88001f3127c0 28 ksoftirqd/3
0xffff88001f314240 30 kworker/3:0H
0xffff88001f314f80 31 kdevtmpfs
0xffff88001f315cc0 32 netns
0xffff88001dc28000 34 khungtaskd
0xffff88001dc28d40 35 oom_reaper
0xffff88001dc29a80 36 writeback
0xffff88001dc2a7c0 37 kcompactd0
0xffff88001dc2b500 38 ksmd
0xffff88001dc2c240 39 crypto
0xffff88001dc2cf80 40 kintegrityd
0xffff88001dc2dcc0 41 bioset
0xffff88001dc2ea00 42 kblockd
0xffff88001dcd8000 43 ata_sff
0xffff88001dcd8d40 44 md
0xffff88001dcd9a80 45 edac-poller
0xffff88001dcda7c0 46 devfreq_wq
0xffff88001dcdb500 47 watchdogd
0xffff88001dcdc240 48 kworker/1:1
0xffff88001dcdcf80 49 kworker/2:1
0xffff88001dcddcc0 50 kworker/3:1
0xffff88001ddf8000 52 kauditd
0xffff88001ddf8d40 53 kswapd0
0xffff88001ddf9a80 54 bioset
0xffff88001ddfa7c0 55 ecryptfs-kthrea
0xffff88001dff0d40 72 kthrotld
0xffff88001dff1a80 73 acpi_thermal_pm
0xffff88001dff27c0 74 bioset
0xffff88001dff3500 75 bioset
0xffff88001dff4240 76 bioset
0xffff88001dff4f80 77 bioset
0xffff88001dff5cc0 78 bioset
0xffff88001dff6a00 79 bioset
0xffff88001dff0000 80 bioset
0xffff88001d660000 81 bioset
0xffff88001d660d40 82 scsi_eh_0
0xffff88001d661a80 83 scsi_tmf_0
---Type <return> to continue, or q <return> to quit---
0xffff88001d6627c0 84 scsi_eh_1
0xffff88001d663500 85 scsi_tmf_1
0xffff88001d718d40 91 ipv6_addrconf
0xffff88001d71dcc0 104 charger_manager
0xffff88001d71a7c0 105 bioset
0xffff88001d71ea00 106 bioset
0xffff88001d71c240 107 bioset
0xffff88001d719a80 110 jbd2/sda-8
0xffff88001d718000 111 ext4-rsv-conver
0xffff88001ddfdcc0 123 kworker/1:1H
0xffff88001ddfcf80 124 kworker/2:1H
0xffff88001ddfc240 127 kworker/0:1H
0xffff88001f350d40 135 kworker/3:2
0xffff88001dea4240 137 kworker/1:2
0xffff88001d0b0d40 140 systemd-journal
0xffff88001dea27c0 142 kworker/2:2
0xffff88001dea0d40 146 kworker/0:3
0xffff88001ded6a00 153 systemd-udevd
0xffff88001dea0000 156 kworker/3:1H
0xffff88001dea5cc0 227 cron
0xffff88001dea1a80 229 rsyslogd
0xffff88001ded0d40 235 in:imuxsock
0xffff88001ded0000 236 in:imklog
0xffff88001ded27c0 237 rs:main Q:Reg
0xffff88001ded1a80 233 agetty
0xffff88001c5d8d40 234 login
0xffff88001dea6a00 243 bash
0xffff88001dea3500 248 kworker/u8:2
0xffff88001c5d9a80 251 kworker/0:1
0xffff88001c5dc240 445 kworker/u8:1
0xffff88001c5ddcc0 452 kworker/u8:0
```
