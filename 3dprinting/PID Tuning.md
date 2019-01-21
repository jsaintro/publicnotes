
# PID Tuning

based on https://reprap.org/wiki/PID_Tuning

## Tune your hotend
1. Run the following gcode

        M303 E0 S200 C8

    This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D

2. Update Marlin

## Tune your heatbed

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjYwNjQ0NjY5LC01MjA3MjE3NjBdfQ==
-->