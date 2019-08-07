# Configure Marlin Firmware
1. Open up Arduino IDE
2. Install TMC2130 Library
Tools/Manage Library
4. Select configuration.h
```
#define MOTHERBOARD BOARD_EINSY_RAMBO

#define X_DRIVER_TYPE  TMC2130
#define Y_DRIVER_TYPE  TMC2130
#define Z_DRIVER_TYPE  TMC2130

#define E0_DRIVER_TYPE TMC2130

```

3. Inst
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5MzI3NzE2MF19
-->