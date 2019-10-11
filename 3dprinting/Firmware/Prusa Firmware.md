
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

# Build the Firmware
1. Clone the repo
	```
	git clone https://github.com/prusa3d/Prusa-Firmware.git
	```
2. Fix Dos CR/LF silliness
      ```
   find . -type f -print0 | xargs -0 dos2unix
   ```
3. Select the MK3 variant (1)
4. Select Eng Language Copy variants/1_75mm_MK3-RAMBo10a-E3Dv6full.h To Configuration_prusa.h:
5. vi config.h
    #define LANG_MODE              0
6. Fix windows cr/lf's
   find . -type f -print0 | xargs -0 dos2unix
7. Compile and install
   run ./PF-build.sh from main dir.
   Bin will be in Prusa-Firmware-Build directory names *.hex
   Flash using prusa slicer
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk5Njk1MDE3MCwtNjUxMjAzODU5LDE2Mj
A2MTE4MzIsLTQxMjcyNjE4NiwtNTg2MjA3MzM0LDgwMTQ3Mzc2
NSwtMzk2NTkzNTk4LDY5ODExMzI2MV19
-->