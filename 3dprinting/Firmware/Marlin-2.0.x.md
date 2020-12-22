## Dependencies
1. Instally missing python modules

        sudo apt-get install python3-distutils
   
## Install VScode for linux
1. sudo apt install snapd
2. sudo snap install --classic code
3. Logout and log back in
4. now search for vscode you should see the icon and when you run it you can then favorite it
5. Install the platformIO IDE plugin from inside the vscode
		1. select extensions from the Left bar (Blocky thing)
		2. Search for `PlatformIO IDE`
		3. Select Install
6. Setup a git repository clone
	1. Select the Ant icon on the left bar
7. Select "Clone git project"

        https://github.com/MarlinFirmware/Marlin.git
        
8. Save somewhere sensible

        gitstuff
        
9. Open the project
10. Select your branch
	1. From the blue status bar on the bottom left most (Says "2.0.x" initially).  Select "2.0.7.2" Currently  
11. edit platformio.ini and select your environment (Default for mega2560 is fine for ramps.
12. Configure
    1. Edit Marlin/Configuration.h
    2. Edit Marlin/Configuration_adv.h
  

## Flash
Add your user to the dialout group so that you can access the serial interface

    sudo adduser *myuserid* dialout

You should now be able to build and flash without issue 

Select the ant
Under project tasks
default
build all
upload all

or ... click the check mark on the botton task bar followed by the right arrow on the bottom task bar
probably have to be connected to usb first.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4NDY3NDUyMSwtODcwMDMxODQ4LDk1Mz
AyMzMzNiwtNzY4NDExNTE1LC01MDkyMTE0NjMsMTk2MjYxMjAy
OCwtODA5NjM2Njg3LDU2ODQ1MzAwMCwtMTM4NDYxMDEwLDE4ND
A3MDI3NTcsLTExNTA3MjQ2MjAsLTczODg2ODk5NCwxMTM1NzYy
MzA3LDEyMTM1MjIxMDEsMTE2MjU3Mzk0NywtNDgzODY3ODk1XX
0=
-->