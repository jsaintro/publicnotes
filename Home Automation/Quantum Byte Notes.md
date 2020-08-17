

This has a 32 bit eufi boot loader and 64 bit processor so you need special os builds that support mixed 32 bit eufi with 64 bit oses.

Fedora can do this no problem
Debian has support for this in the multi-arch installer [http://mirrors.gigenet.com/debian-cd/10.5.0/multi-arch/iso-cd/](http://mirrors.gigenet.com/debian-cd/10.5.0/multi-arch/iso-cd/)
It must be multiarch (Say both amd64-i386 (only the netinstall appears to do this)
https://cdimage.debian.org/debian-cd/current/multi-arch/iso-cd/debian-10.5.0-amd64-i386-netinst.iso

Ubuntu does not work (Don't bother)
There's a complex process to try and get Ubuntu to work here
[https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)
You tried it but it it didn't work
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDI1NTMxNzAxLDE4MjQ2OTk0MjIsOTQyMD
MyNzcxXX0=
-->