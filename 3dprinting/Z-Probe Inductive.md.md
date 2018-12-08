# Stats
* Weight ??g
* LJ8A3-2-Z-BX-5V
* DC 5V M8 2mm NPN NO LJ8A3-2-Z/BX-5V Inductive Proximity Sensor Switch

# Wiring
Blue = Ground
Brown = 5V+
Black = Sense

# Surface Notes

With 3mm alu bed has about a 2mm detection distance.  So PEI sheet must be very thin

# Mechanical Placement
1. Double paper over and place under extruder
2. Lower extruder till it touches paper in 0.1mm increments
3. Raise extruder .1mm
4. See if sensor has triggred with M119 (Z endtop triggered)
5. If not then rotate sensor 1/4 and check M119 repeat till triggered
6. G28
7. Remove a couple of slips of paper and faster there

# Test sensor functionality
1. With sensor untriggered
    Send M119 to see if Z endstop is untriggered
    ```
    Reporting endstop status
    x_min: open
    y_min: open
    z_min: open
    ok
    ```

2. Trigger sensor
    ```
    Reporting endstop status
    x_min: open
    y_min: open
    z_min: TRIGGERED
    ok
    ```

3. Adjust pot ccw greater distance from bed cw shorter distance from bed.
Adjust so it triggers at 2mm from bed.  Use stacked business cards to determine 2 mm

Use G92Z{distance) to set position of z independent of probe

# Calculate z height distance
1. Disable min software endstops

        #define min_software_endstops false

2. Flash marlin with 1 offset
    1. Open Anduino IDE
    2. Edit configure.h
 
            Z_PROBE_OFFSET_FROM_EXTRUDER = 0
    3.  Save and upload
        
3. Preheat bed to operating temp (ABS = 100c PLA = 60c?)
4. Get Z probe trigger distance
    1. Run `G28` to home Z
    2. Descend to Z0 location `G0 Z0`
5. Descent to 1st layer distance
     1. Place 0.063 feeler guage under extruder
     2. descent in .1 increments while moving the feeler back and forth waiting until you feel it pinch
     3.  Record Z for M114 (Ex. -0.40)
6.  This number represents the distance *below* the nozzle tip that the sensor triggered
7. Set Z_PROBE_OFFSET_FROM_EXTRUDER to negative value of the distance Ex. Distance = 0.40 = -0.40 Z_PROBE_OFFSET
    Note: We do the negative because the probe is triggering below the nozzle tip (Always the case with a static probe)
8. Test
    Use a simple test print and see if 1st layer is going town (No gaps between lines and not peeling up in spots
9.  Fine tune: If it's still not perfect add another 0.1 so for our example that would be -0.50
    Note: Higher negative numbers move the extruder closer to the bed (Ex. -0.50 move the extruder closer to the bed vs -0.40. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzYxODg0MjkyLC0xNjIwNjE5ODIzLDUzND
E3NDI2OCwtMTk3MzYzNTUzMywtMTkwMjQzNDQyMCw1ODcxNTEy
MjhdfQ==
-->