
## Setup the libs in the arduino IDE
2. Get the board config
	1.  Open Arduino and navigate to File -> Preferences -> Settings
	2. To the text field  `"Additional Boards Manager URLSs"`  add `https://raw.githubusercontent.com/prusa3d/Arduino_Boards/master/IDE_Board_Manager/package_prusa3d_index.json`
-   Open Board manager (`Tools->Board->Board manager`), and install  `Rambo`
3. Add compiler options
```
vi /opt/arduino-{version}/hardware/arduino/avr/platform.txt
compiler.c.elf.flags={compiler.warning_flags} -Os -g -flto -fuse-linker-plugin -Wl,-u,vfprintf -lprintf_flt -lm -Wl,--gc-sections
```
Note: `-Wl,-u,vfprintf -lprintf_flt -lm` is what was added
Note: You can probably skip this for just marlin
Note: make sure you use the right version for the arduino ide your using.  Aka if you upgrade.
5. Install TMC2130 Library
Sketch/Include Library/Manage Libraries
Search for `TMC2130Stepper`
Install the TMC2130Stepper library

1. Clone the repo
2. Copy variants/1_75mm_MK3-RAMBo10a-E3Dv6full.h Configuration_prusa.h
3. vi config.h
    #define LANG_MODE              0
4. 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU5NDg1Mjk0XX0=
-->