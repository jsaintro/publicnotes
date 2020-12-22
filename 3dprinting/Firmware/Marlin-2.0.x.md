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
	1. From the blue status bar on the bottom left most (Says "2.0.x" initially).  Select "2.0.1"  
11. edit platformio.ini and select your environment (Default for mega2560 is fine for ramps.
12. Configure

## Flash
Add your user to the dialout group so that you can access the serial interface

    sudo adduser *myuserid* dialout

You should now be able to build and flash without issue 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA0NDU2MTc0NSwtNzY4NDExNTE1LC01MD
kyMTE0NjMsMTk2MjYxMjAyOCwtODA5NjM2Njg3LDU2ODQ1MzAw
MCwtMTM4NDYxMDEwLDE4NDA3MDI3NTcsLTExNTA3MjQ2MjAsLT
czODg2ODk5NCwxMTM1NzYyMzA3LDEyMTM1MjIxMDEsMTE2MjU3
Mzk0NywtNDgzODY3ODk1XX0=
-->