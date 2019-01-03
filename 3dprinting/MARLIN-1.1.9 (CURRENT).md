[TOC]

## Requirements

* ARDUINO IDE is installed and communicating (See ARDUINO Doc)

## Install U8glib Library
1.  Open IDE
2. Select "Tools/Library Manager"
3. Search for "U8glib"
4. Install latest version

## Install Marlin
1. Download the latest stable Marlin from here
* [Marlin Project](https://github.com/MarlinFirmware/Marlin/releases)
* This is the one we're currently on
[1.1.9](https://github.com/MarlinFirmware/Marlin/archive/1.1.9.zip)
2. move to Documents directory and extract the source

        mkdir ~/Documents/3dPrinter
        mv ~/Downloads/Marlin-1.1.0-RC8.zip ~/Documents/3dPrinter
        unzip Marlin-1.1.0-RC8.zip
        
3. Open in Arduino IDE
    "File/Open" select "Documents/3dPrinter/Marlin-1.1.0-RC8/Marlin/Marlin.ino"
    
# Configure Marlin for Wilson TS
## Configuration.h
1. Change author
```
#define STRING_CONFIG_H_AUTHOR "(jsaintrocc, default config)" // Who made the changes.
```
1. Select the Arduino Mega Mainboard
```
#ifndef MOTHERBOARD
  #define MOTHERBOARD BOARD_RAMPS_14_EFB
#endif
```
1. Define the printer name
```
#define CUSTOM_MACHINE_NAME "Wilson TS"
```
1. Define the Extruder/Bed Temp thermistor
```
#define TEMP_SENSOR_0 1 // I think this is the current best choice for ebay ntc 3950.  Need to confirm with thermocouple.
#define TEMP_SENSOR_1 0
#define TEMP_SENSOR_BED 1 //65 at set 60 set 110 at set 110
```
1. Set higher cutoff for extruder heat
```
#define HEATER_0_MAXTEMP 280
```
1. Set PID (Helps stabilze heating quicker)
```
    // Wilson TS
    #define  DEFAULT_Kp 18.68
    #define  DEFAULT_Ki 1.11
    #define  DEFAULT_Kd 78.83
```
1. Set PID for Bed
```
    // Wilson TS Bed
    #define  DEFAULT_bedKp 240.60
    #define  DEFAULT_bedKi 14.98
    #define  DEFAULT_bedKd 965.80
```
1. Tweak the thermal runaway for the heatbed
Edit in Configuration_adv.h
```
#define THERMAL_RUNAWAY_PROTECTION_BED_PERIOD 60 //in seconds for 110 bed temp
#define THERMAL_RUNAWAY_PROTECTION_BED_HYSTERESIS 4 // in degree Celsius for 110 bed temp
```
1. Invert the extruder stepper (in Configuration.h)
```
#define INVERT_E0_DIR true
```
1. Set the travel limits (Probably need to retune this)
```
#define X_MIN_POS -5
#define Y_MIN_POS -10
#define Y_MAX_POS 190
#define Z_MAX_POS 165
```
Note: This is after adjusting your Y table far left

1. Fix Axis Inversion for Wilson
```
#define INVERT_X_DIR true
#define INVERT_Y_DIR false
#define INVERT_Z_DIR true
```
Note Might want to just flip every the stepper cables here
1. Fix Endstop inversion for Wilson
```
#define X_MIN_ENDSTOP_INVERTING true
#define Y_MIN_ENDSTOP_INVERTING true
#define Z_MIN_ENDSTOP_INVERTING true


```
Note: Should probably flip enstonps and uninvert these (Would be safer?)
1. Set the homing speeds to something fast yet reasonable
```
#define HOMING_FEEDRATE_XY (150*60)
#define HOMING_FEEDRATE_Z  (3*60)
```
Note: might want to see if z can be set to default (4*60)
1. Define servo steps
```
#define DEFAULT_AXIS_STEPS_PER_UNIT   {80,80,3935,102}  // Wilson TS W/.4 nozzle (Fine Tuned)
// Note: less steps for small, more for bigger
```
1. Define the max feedrates
```
#define DEFAULT_MAX_FEEDRATE          {200, 200, 3, 25}    // (mm/sec)
#define DEFAULT_MAX_ACCELERATION      {2000,2000,100,10000}
```
Note: Need to revisit these settings esp z which could be set at default if we increase stepper current??
1. Jerk settings
```
#define DEFAULT_XYJERK                25.0    // (mm/sec)
#define DEFAULT_ZJERK                 0.6     // (mm/sec) 20% of 3mm/sec max
```
1. Set some preheat settings
```
#define PREHEAT_1_TEMP_BED     50
#define PREHEAT_2_TEMP_HOTEND 263
#define PREHEAT_2_TEMP_BED    105
```
# LCD Setup
1. Enable the LCD

        #define REPRAP_DISCOUNT_FULL_GRAPHIC_SMART_CONTROLLER

3. Fix Encoder Direction

        #define REVERSE_ENCODER_DIRECTION
        #define REVERSE_MENU_DIRECTION

4. Add SD support

        #define SDSUPPORT

5. Save the project
    File/Save

## Compile the code
1. Sketch/Verify/compile

Note: Lots of warnings are normal
## Upload
1. Sketch/Upload (This will take about 1 minute) You'll see the LCD screen blink when it's done
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMDYxNDQ2MjQsMTcyMzgzOTc2MiwtMz
c2ODI4ODgyLDMyMjc3OTk4NCwxNzE1NTc4NDg4XX0=
-->