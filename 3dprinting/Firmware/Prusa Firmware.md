
## Setup the libs in the arduino IDE (SKIP BECAUSE YOUR USING shell script)
2. Get the board config
	1.  Open Arduino and navigate to File -> Preferences -> Settings
	2. To the text field  `"Additional Boards Manager URLSs"`  add `https://raw.githubusercontent.com/prusa3d/Arduino_Boards/master/IDE_Board_Manager/package_prusa3d_index.json`
-   Open Board manager (`Tools->Board->Board manager`), and install  `Prusa Research AVR MK3 RAMBo EINSy board`
3. Add compiler options
```
vi /opt/arduino-{version}/hardware/arduino/avr/platform.txt
compiler.c.elf.flags={compiler.warning_flags} -Os -g -flto -fuse-linker-plugin -Wl,-u,vfprintf -lprintf_flt -lm -Wl,--gc-sections
```
Note: `-Wl,-u,vfprintf -lprintf_flt -lm` is what was added
Note: make sure you use the right version for the arduino ide your using.  Aka if you upgrade.
4. Install TMC2130 Library
Sketch/Include Library/Manage Libraries
Search for `TMC2130Stepper`
Install the TMC2130Stepper library

## Get the Firmware
1. Clone the repo
	```
	git clone https://github.com/prusa3d/Prusa-Firmware.git
	```
2. Select the version
    ```
    cd Prusa-Firmware
    git checkout v3.8.0
    ```
3. Fix Dos CR/LF silliness
      ```
   find . -type f -print0 | xargs -0 dos2unix
   ```

## Configure
1. Copy the configuration file
     ```
3. Run the build script
   ```
   ./PF-build.sh
   ```
	5. Select the MK3 variant (1)
	6. Select Englist Only (2)
	7. Dev_status (1) Language
4. Bin will be in PF-Build-Hex directory named *.hex
5. Flash using prusa slicer (or octopi)
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgxMDcxNTk1NCwyMDY2NTg2MzExLC0xND
U3ODk4NDExLC02NTEyMDM4NTksMTYyMDYxMTgzMiwtNDEyNzI2
MTg2LC01ODYyMDczMzQsODAxNDczNzY1LC0zOTY1OTM1OTgsNj
k4MTEzMjYxXX0=
-->