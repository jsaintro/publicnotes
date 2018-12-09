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
4. See if sensor has triggered with M119 (Z endtop triggered)
5. If not then rotate sensor 1/4 and check M119 repeat till triggered
6. Repeat steps 1 till sensor triggers
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

## Calculate z probe offset
1. Prep
	 * Make sure 1st layer height and width in slicer is set to 100%
	 * Bring heat bed up to operating temp (ABS = 105c, PLA = 60c)

2. Zero out offset (temporarily)

         M851 Z0 

3. Wait for heated bed to come up to temp
4. Get Z probe trigger distance
    1. Run `G28` to home Z
    2. Descend to Z0 location `G0 Z0`
    3. Place piece of paper under extruder (old inst was to use 0.063 feeler gauge)
    4. Descend in 0.1mm increments while moving paper back and forth waiting until you feel it pinch (noticeable grab)
    5. Record Z offset
            
            M114
         Ex. -0.40
    6.  This number represents the distance *below* the nozzle tip that the sensor triggered
5. Calculate z offest + fudge factor of -0.08??.  (Ex -0.30 + -0.08 = -0.38)
    the more negative the closer the extruder is to the build plate 
    Note: We do the negative because the probe is triggering below the nozzle tip (Always the case with a static probe)
6. Temporarily set the new z offset

         M851 Z-0.40

7. Run a test print
   * You should have COMPLETE coverage on the 1st layer no gaps
   * It's better to over be a little over extruded on the 1st layer then under extruded
 8. If there we're gaps add a correction of -0.05 and repeat (For our example -0.40 + -0.05 = -0.45
 
          M851 Z-0.45
          G28
          G0 Z1 // Check to make sure you're not crashing into the bed
          G0 Z0.5 // Should be getting close now
          G0 Z0.1 // Sould be pretty much touching Feeler should just fit under 
    Use a simple test print and see if 1st layer is going town (No gaps between lines and not peeling up in spots
9.  Fine tune: If it's still not perfect add another 0.1 so for our example that would be -0.50
    Note: Higher negative numbers move the extruder closer to the bed (Ex. -0.50 move the extruder closer to the bed vs -0.40. 
10. Use M851 to temp get set offset
11. Save offset to firmware
lash marlin with 1 offset
    1. Open Anduino IDE
    2. Edit configure.h
 
            Z_PROBE_OFFSET_FROM_EXTRUDER = 0
    3.  Save and upload
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNjYxMzUwNTksMTU2ODI1MTMwNSwtOD
c3MzkzNjA3LDExMzQ4ODk1OTUsMTgyMTgzODU2NCwyMDU1NTM5
MTE5LDk5MzI2MjkzNSwxNjIzMTQ1MjI3LDEwNDk5MzYxMzksLT
E2MjA2MTk4MjMsNTM0MTc0MjY4LC0xOTczNjM1NTMzLC0xOTAy
NDM0NDIwLDU4NzE1MTIyOF19
-->