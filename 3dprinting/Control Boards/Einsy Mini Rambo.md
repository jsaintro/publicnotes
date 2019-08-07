# Configure Marlin Firmware
1. Open up Arduino IDE
2. Get the board config
	1.  Open Arduino and navigate to File -> Preferences -> Settings
	2. To the text field  `"Additional Boards Manager URLSs"`  add `https://raw.githubusercontent.com/prusa3d/Arduino_Boards/master/IDE_Board_Manager/package_prusa3d_index.json`
-   Open Board manager (`Tools->Board->Board manager`), and install  `Prusa Research AVR MK3 RAMBo EINSy board`
3. Add compiler options
```
vi /opt/arduino-1.8.7/hardware/arduino/avr/platform.txt
compiler.c.elf.flags={compiler.warning_flags} -Os -g -flto -fuse-linker-plugin -Wl,-u,vfprintf -lprintf_flt -lm -Wl,--gc-sections
```
Note: `-Wl,-u,vfprintf -lprintf_flt -lm` is what was added
5. Install TMC2130 Library
Tools/Manage Library
6. Select configuration.h
```
#define MOTHERBOARD BOARD_EINSY_RAMBO

#define X_DRIVER_TYPE  TMC2130
#define Y_DRIVER_TYPE  TMC2130
#define Z_DRIVER_TYPE  TMC2130

#define E0_DRIVER_TYPE TMC2130

```

3. Inst
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDk5MDAzOTEsMTEzOTI3MjAxOCwxMz
kzMjc3MTYwXX0=
-->