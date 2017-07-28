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

```ldconfig``` utility manages the cache for mapping dynamic library names to actual paths.

```
root@localhost:~# ldconfig -p
121 libs found in cache `/etc/ld.so.cache'
	libz.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libz.so.1
	libxtables.so.10 (libc6,x86-64) => /lib/libxtables.so.10
	libuuid.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libuuid.so.1
	libutil.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libutil.so.1
	libustr-1.0.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libustr-1.0.so.1
	libusb-0.1.so.4 (libc6,x86-64) => /lib/x86_64-linux-gnu/libusb-0.1.so.4
	libusb-0.1.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libusb-0.1.so.4
	libudev.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libudev.so.1
	libtinfo.so.5 (libc6,x86-64) => /lib/x86_64-linux-gnu/libtinfo.so.5
	libtic.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libtic.so.5
	libthread_db.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libthread_db.so.1
	libtasn1.so.6 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libtasn1.so.6
	libsystemd.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libsystemd.so.0
	libstdc++.so.6 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libstdc++.so.6
	libssl.so.1.0.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0
	libss.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libss.so.2
	libsmartcols.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libsmartcols.so.1
	libslang.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libslang.so.2
	libsigc-2.0.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libsigc-2.0.so.0
	libsepol.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libsepol.so.1
	libsemanage.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libsemanage.so.1
	libselinux.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libselinux.so.1
	librt.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/librt.so.1
	libresolv.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libresolv.so.2
	libreadline.so.6 (libc6,x86-64) => /lib/x86_64-linux-gnu/libreadline.so.6
	libp11-kit.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0
	libpthread.so.0 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libpthread.so.0
	libpsl.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libpsl.so.0
	libprocps.so.3 (libc6,x86-64) => /lib/x86_64-linux-gnu/libprocps.so.3
	libpopt.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libpopt.so.0
	libpipeline.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libpipeline.so.1
	libperl.so.5.20 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libperl.so.5.20
	libpcreposix.so.3 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libpcreposix.so.3
	libpcre.so.3 (libc6,x86-64) => /lib/x86_64-linux-gnu/libpcre.so.3
	libpcprofile.so (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libpcprofile.so
	libpanelw.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libpanelw.so.5
	libpanel.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libpanel.so.5
	libpamc.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libpamc.so.0
	libpam_misc.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libpam_misc.so.0
	libpam.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libpam.so.0
	libnss_nisplus.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_nisplus.so.2
	libnss_nis.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_nis.so.2
	libnss_hesiod.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_hesiod.so.2
	libnss_files.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_files.so.2
	libnss_dns.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_dns.so.2
	libnss_compat.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnss_compat.so.2
	libnsl.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libnsl.so.1
	libnfnetlink.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libnfnetlink.so.0
	libnewt.so.0.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libnewt.so.0.52
	libnettle.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libnettle.so.4
	libnetfilter_acct.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libnetfilter_acct.so.1
	libncursesw.so.5 (libc6,x86-64) => /lib/x86_64-linux-gnu/libncursesw.so.5
	libncurses.so.5 (libc6,x86-64) => /lib/x86_64-linux-gnu/libncurses.so.5
	libmount.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libmount.so.1
	libmnl.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libmnl.so.0
	libmenuw.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libmenuw.so.5
	libmenu.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libmenu.so.5
	libmemusage.so (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libmemusage.so
	libm.so.6 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libm.so.6
	liblzma.so.5 (libc6,x86-64) => /lib/x86_64-linux-gnu/liblzma.so.5
	liblognorm.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/liblognorm.so.1
	liblogging-stdlog.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/liblogging-stdlog.so.0
	libkmod.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libkmod.so.2
	libjson-c.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libjson-c.so.2
	libisccfg-export.so.90 (libc6,x86-64) => /lib/x86_64-linux-gnu/libisccfg-export.so.90
	libisc-export.so.95 (libc6,x86-64) => /lib/x86_64-linux-gnu/libisc-export.so.95
	libirs-export.so.91 (libc6,x86-64) => /lib/x86_64-linux-gnu/libirs-export.so.91
	libip6tc.so.0 (libc6,x86-64) => /lib/libip6tc.so.0
	libip4tc.so.0 (libc6,x86-64) => /lib/libip4tc.so.0
	libiptc.so.0 (libc6,x86-64) => /lib/libiptc.so.0
	libipq.so.0 (libc6,x86-64) => /lib/libipq.so.0
	libidn.so.11 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libidn.so.11
	libicuuc.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicuuc.so.52
	libicutu.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicutu.so.52
	libicutest.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicutest.so.52
	libiculx.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libiculx.so.52
	libicule.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicule.so.52
	libicui18n.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicui18n.so.52
	libicuio.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicuio.so.52
	libicudata.so.52 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libicudata.so.52
	libhogweed.so.2 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libhogweed.so.2
	libhistory.so.6 (libc6,x86-64) => /lib/x86_64-linux-gnu/libhistory.so.6
	libgpg-error.so.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libgpg-error.so.0
	libgnutls-openssl.so.27 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libgnutls-openssl.so.27
	libgnutls-deb0.so.28 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libgnutls-deb0.so.28
	libgmp.so.10 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libgmp.so.10
	libgdbm_compat.so.3 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libgdbm_compat.so.3
	libgdbm.so.3 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libgdbm.so.3
	libgcrypt.so.20 (libc6,x86-64) => /lib/x86_64-linux-gnu/libgcrypt.so.20
	libgcc_s.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libgcc_s.so.1
	libformw.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libformw.so.5
	libform.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libform.so.5
	libffi.so.6 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libffi.so.6
	libe2p.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libe2p.so.2
	libext2fs.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libext2fs.so.2
	libestr.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libestr.so.0
	libdns-export.so.100 (libc6,x86-64) => /lib/x86_64-linux-gnu/libdns-export.so.100
	libdl.so.2 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libdl.so.2
	libdevmapper.so.1.02.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libdevmapper.so.1.02.1
	libdebconfclient.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libdebconfclient.so.0
	libdb-5.3.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libdb-5.3.so
	libcryptsetup.so.4 (libc6,x86-64) => /lib/x86_64-linux-gnu/libcryptsetup.so.4
	libcrypto.so.1.0.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
	libcrypt.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libcrypt.so.1
	libcom_err.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libcom_err.so.2
	libcidn.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libcidn.so.1
	libcap.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libcap.so.2
	libc.so.6 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libc.so.6
	libbz2.so.1.0 (libc6,x86-64) => /lib/x86_64-linux-gnu/libbz2.so.1.0
	libboost_iostreams.so.1.55.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libboost_iostreams.so.1.55.0
	libblkid.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libblkid.so.1
	libaudit.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libaudit.so.1
	libattr.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libattr.so.1
	libapt-private.so.0.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libapt-private.so.0.0
	libapt-pkg.so.4.12 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12
	libapt-inst.so.1.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libapt-inst.so.1.5
	libanl.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libanl.so.1
	libacl.so.1 (libc6,x86-64) => /lib/x86_64-linux-gnu/libacl.so.1
	libSegFault.so (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libSegFault.so
	libBrokenLocale.so.1 (libc6,x86-64, OS ABI: Linux 2.6.32) => /lib/x86_64-linux-gnu/libBrokenLocale.so.1
	ld-linux-x86-64.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
```
