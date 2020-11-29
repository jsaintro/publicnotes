# Get ubuntu version
## Linux (Ubuntu 20.10)
1. Install the latest driver
    displaylik-driver-5.3.1.34 (As of this writing)
2. Use patched version of Xserver
	https://www.displaylink.org/forum/showthread.php?t=67148
    Note: This is for 20.04 but also works for 20.10
3. Lock this version with 
    `sudo apt-mark hold xserver-xorg-core` should work.
     To undo this, do `apt-mark unhold xserver-xorg-core`

## Troubleshooting
1. Extract the drivers
```
./displaylink-driver-5.3.1.34.run --noexec --keep
cd displaylik-driver-5.3.1.34
sudo ./displaylist-installer install
```

Full procedure here
https://www.displaylink.org/forum/showpost.php?p=90853&postcount=2

https://www.displaylink.org/forum/showthread.php?t=67148
https://gitlab.freedesktop.org/xorg/xserver/-/issues/1028
https://bugs.launchpad.net/xorg-server/+bug/1875015

https://www.displaylink.org/forum/showthread.php?t=67148

Error
```
Installing

[ Installing EVDI ]
[[ Installing EVDI DKMS module ]]

Creating symlink /var/lib/dkms/evdi/1.7.0/source ->
                 /usr/src/evdi-1.7.0

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.8.0-7630-generic all INCLUDEDIR=/lib/modules/5.8.0-7630-generic/build/include KVERSION=5.8.0-7630-generic DKMS_BUILD=1...(bad exit status: 2)
ERROR (dkms apport): binary package for evdi: 1.7.0 not found
Error! Bad return status for module build on kernel: 5.8.0-7630-generic (x86_64)
Consult /var/lib/dkms/evdi/1.7.0/build/make.log for more information.
ERROR: Failed to install evdi/5.3.1.34 to the kernel tree.
```


For Ubuntu

lsb_release -a

You have an Intel video card
Download the driver here
http://www.displaylink.com/downloads/ubuntu

mkdir ds
mv DisplayLink\ USB\ Graphics\ Software\ for\ Ubuntu\ 5.2.zip ds/
cd ds/
unzip DisplayLink\ USB\ Graphics\ Software\ for\ Ubuntu\ 5.2.zip 
chmod +x displaylink-driver-5.2.14.run 
sudo ./displaylink-driver-5.2.14.run 

# OSX Version
Note: Don't upgrade to Big Sur 11.0 until DisplayLink Manager Graphics Connectivity supports clamshell mode.

## Recommended Release
Legacy Releases 5.2.5 for Catalina 10.15 & Mojave 10.14
https://www.displaylink.com/downloads/macos


In chrome disable hardware accelleration (For youtube to work)
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzQ0NDkwMzE2LC0xMTA2ODMzMzg2LC0xOD
k5NjIwMjk4LC0xNTAyNzU0Mzg2LDYzMzM5ODgyMSwxMTYxNzY2
ODk2LDE4MTg2MTI5MywxOTczNjU4MTkzLDExMzIyNjE5NzksLT
IwMjQwNjkzMTUsMTY0MjM0MzY5Miw5MDMxMTI5NjFdfQ==
-->