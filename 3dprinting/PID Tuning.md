
# PID Tuning

based on https://reprap.org/wiki/PID_Tuning

## Enable PID for both extruder and bed
1. Edi

## Tune your hotend
1. Run the following gcode

        M303 E0 S200 C8

    This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D

    Final output will be the lines you need to add to your marlin config

2. Update Marlin
	1. Edit Configuration.h

            #define PIDTEMP
            #define DEFAULT_Kp <P>
            #define DEFAULT_Ki <I>
            #define DEFAULT_Kd <D>
## Tune your heatbed
1. Run the following gcode

        M303 E-1 S60 C8
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM3ODAyMDc1MiwyNjA2NDQ2NjksLTUyMD
cyMTc2MF19
-->