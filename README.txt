TIP1: UDT librarry
---------------------------
please use the included UDT library package 
to build udtgate 

TIP2: Make
----------------------------
Some make problems with older
libtool/automake/autoconf versions:

To fix the problem:

make distclean (if Makefile exists)

libtoolize --force --copy
aclocal -I /usr/local/share/libtool/libltdl
autoconf
automake --add-missing  


TIP3: UDP buffer size fix for FreeBSD
-------------------------------------
native UDT application use default UDP receive 
buffer about 10M - much more then default maximal
buffer size in FreeBSD

To fix it unrease max UDP buffer 
sysctl -w kern.ipc.maxsockbuf=12000000

TIP4: Native thread library in FreeBSD
--------------------------------------
Mutex problem take place in pthread library
for FreeBSD 6.X.
For FreBSD 6.X wrap pthread to thread library

File /etc/libmap.conf:

[udtrelay]
libpthread.so.2 libthr.so.2

