# Configure Marlin Firmware
1. Open up Arduino IDE
2. Get the board config
	1.  Open Arduino and navigate to File -> Preferences -> Settings
	2. To the text field  `"Additional Boards Manager URLSs"`  add `https://raw.githubusercontent.com/ultimachine/ArduinoAddons/master/package_ultimachine_index.json`
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

6. Select configuration.h
```
#define MOTHERBOARD BOARD_EINSY_RAMBO

#define X_DRIVER_TYPE  TMC2130
#define Y_DRIVER_TYPE  TMC2130
#define Z_DRIVER_TYPE  TMC2130

#define E0_DRIVER_TYPE TMC2130

#define REPRAP_DISCOUNT_SMART_CONTROLLER
//#define MESH_EDIT_GFX_OVERLAY
```

3. Inst
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ4NDI5OTA0MiwxMDg4MDg2MzY4LC02Nz
UwOTUwMTEsMTYzNzcwOTczOSwtNTM4OTAyNzEyLC0xMTA5OTAw
MzkxLDExMzkyNzIwMTgsMTM5MzI3NzE2MF19
-->