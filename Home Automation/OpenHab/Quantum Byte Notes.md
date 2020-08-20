## ScrewUP
Don't disable the internal graphics card You'll never get it back and it essentailly means the device is bricked. Also you might need an HDMI dummy connector to run headless.

## Linux Install

Note: This has a 32 bit eufi boot loader and 64 bit processor so you need special os builds that support mixed 32 bit eufi with 64 bit oses. Fedora and Debain can do this but Ubuntu doesn't work

### Debian
Debian has support for this in the multi-arch installer [http://mirrors.gigenet.com/debian-cd/10.5.0/multi-arch/iso-cd/](http://mirrors.gigenet.com/debian-cd/10.5.0/multi-arch/iso-cd/)
It must be multiarch (Say both amd64-i386 (only the netinstall appears to do this)
https://cdimage.debian.org/debian-cd/current/multi-arch/iso-cd/debian-10.5.0-amd64-i386-netinst.iso
Do the net install (Used the wired nic)
Deselect everything accept for SSH server and core utilities

### Fedora
Fedora can do this no problem


### Ubuntu
Ubuntu does not work (Don't bother)
There's a complex process to try and get Ubuntu to work here
[https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec](https://medium.com/@realzedgoat/a-sorta-beginners-guide-to-installing-ubuntu-linux-on-32-bit-uefi-machines-d39b1d1961ec)
You tried it but it it didn't work

## Initial System Config (Debian)
Install sudo
apt-get install sudo
add user to sudoers
usermod -aG sudo jsaintrocc
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk1NzIwOTg5OV19
-->