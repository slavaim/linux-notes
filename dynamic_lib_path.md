Dynamic library path is defined by LD_LIBRARY_PATH or/and ```/etc/ld.so.conf```

```
root@localhost:~# cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf

root@localhost:~# ls -la /etc/ld.so.conf.d/
total 16
drwxr-xr-x  2 root root 4096 Sep 14  2015 .
drwxr-xr-x 52 root root 4096 Jul 28 14:57 ..
-rw-r--r--  1 root root   44 Aug  9  2009 libc.conf
-rw-r--r--  1 root root   68 Aug 30  2015 x86_64-linux-gnu.conf

root@localhost:~# cat /etc/ld.so.conf.d/x86_64-linux-gnu.conf 
# Multiarch support
/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu
```
