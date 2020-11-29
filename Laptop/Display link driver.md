# Get ubuntu version
## Linux (Ubuntu 20.10)
Note: Currently you need to get the master release
https://support.displaylink.com/knowledgebase/articles/679060-porting-the-displaylink-ubuntu-driver-to-other-lin

1. Extract the drivers
```
./displaylink-driver-5.3.1.34.run --noexec --keep
cd displa
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
eyJoaXN0b3J5IjpbLTI2Njc1MDQyLDExNjE3NjY4OTYsMTgxOD
YxMjkzLDE5NzM2NTgxOTMsMTEzMjI2MTk3OSwtMjAyNDA2OTMx
NSwxNjQyMzQzNjkyLDkwMzExMjk2MV19
-->