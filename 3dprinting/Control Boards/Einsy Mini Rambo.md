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
Note: make sure you use the right version for the arduino ide your using.  Aka if you upgrade.
5. Install TMC2130 Library
Sketch/Include Library/Manage Libraries
Search for `TMC2130Stepper`
Install the TMC2130Stepper library

6. Select configuration.h
```
#define BAUDRATE 115200

#define MOTHERBOARD BOARD_EINSY_RAMBO

#define X_DRIVER_TYPE  TMC2130
#define Y_DRIVER_TYPE  TMC2130
#define Z_DRIVER_TYPE  TMC2130

#define E0_DRIVER_TYPE TMC2130

#define REPRAP_DISCOUNT_SMART_CONTROLLER
//#define MESH_EDIT_GFX_OVERLAY
```

7. Edit configuration_adv.h
*From Einsy reprap page*
```
#define R_SENSE           0.11  // R_sense resistor for SilentStepStick2130
```

9. Inst
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg5MjA4NDMzNSwxNDg0Mjk5MDQyLDEwOD
gwODYzNjgsLTY3NTA5NTAxMSwxNjM3NzA5NzM5LC01Mzg5MDI3
MTIsLTExMDk5MDAzOTEsMTEzOTI3MjAxOCwxMzkzMjc3MTYwXX
0=
-->