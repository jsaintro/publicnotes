# Configure Marlin Firmware
## Setup Dependencies
1. Open up Arduino IDE
2. Get the board config
	1.  Open Arduino and navigate to File -> Preferences -> Settings
	2. To the text field  `Additional Boards Manager URLSs`  add
		 `https://raw.githubusercontent.com/ultimachine/ArduinoAddons/master/package_ultimachine_index.json`
	1. Open Board manager (`Tools->Board->Board manager`), and install  `Rambo`

		*Note: if you get an spi.h missing error it's because you're didn't do this*

3. Add compiler options
	```
	vi /opt/arduino-{version}/hardware/arduino/avr/platform.txt
	compiler.c.elf.flags={compiler.warning_flags} -Os -g -flto -fuse-linker-plugin -Wl,-u,vfprintf -lprintf_flt -lm -Wl,--gc-sections
	```
	Note: `-Wl,-u,vfprintf -lprintf_flt -lm` is what was added
	Note: make sure you use the right version for the arduino ide your using.  Aka if you upgrade.

5. Install TMC2130 Library
	1. Navigate to Sketch -> Include Library -> Manage Libraries
	2. Search for `TMC2130Stepper`
	3. Install the `TMC2130Stepper` library

## Einsy Specific Config
1. Select configuration.h
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
#define R_SENSE           0.22  // R_sense resistor for SilentStepStick2130
```

9. Install
<!--stackedit_data:
eyJoaXN0b3J5IjpbODEzNTc1OTU1LC0xMTY5MjIxNzExLC04OT
IwODQzMzUsMTQ4NDI5OTA0MiwxMDg4MDg2MzY4LC02NzUwOTUw
MTEsMTYzNzcwOTczOSwtNTM4OTAyNzEyLC0xMTA5OTAwMzkxLD
ExMzkyNzIwMTgsMTM5MzI3NzE2MF19
-->