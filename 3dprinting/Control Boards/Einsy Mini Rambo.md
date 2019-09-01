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
//#define E0_AUTO_FAN_PIN -1 // Comment this out to enable it??!!
#define R_SENSE           0.22  // R_sense resistor for SilentStepStick2130

#define FILAMENT_LOAD_UNLOAD_GCODES 
```

9. Install
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2NjAzNTk0MywxNDMyNDA3NTA0LDgxMz
U3NTk1NSwtMTE2OTIyMTcxMSwtODkyMDg0MzM1LDE0ODQyOTkw
NDIsMTA4ODA4NjM2OCwtNjc1MDk1MDExLDE2Mzc3MDk3MzksLT
UzODkwMjcxMiwtMTEwOTkwMDM5MSwxMTM5MjcyMDE4LDEzOTMy
NzcxNjBdfQ==
-->