# Stats
* Weight ??g
* LJ8A3-2-Z-BX-5V
* DC 5V M8 2mm NPN NO LJ8A3-2-Z/BX-5V Inductive Proximity Sensor Switch
* I don't this is truly a 5V probe probably 6-36 (There is an LED but it barely lights at 5V)

# Wiring
Blue = Ground
Brown = 5V+
Black = Sense

# Surface Notes

With 3mm alu bed has about a 2mm detection distance.  So PEI sheet must be very thin

# Mechanical Placement
1. Lower extruder till it touches paper in 0.1mm increments
2. Raise extruder .1mm
3. put the thickness of 2 small zip ties under probe and drop probe till it touches zip ties
4. See if sensor has triggered with M119 (Z endtop triggered)
6. Raise in .1 mm increments until the prob stops triggering
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

       //#define MIN_SOFTWARE_ENDSTOP_Z
      or better in gcode do 
      M211 S0 to disable
      M211 S1 to enable

## Calculate z probe offset
1. Prep
	 * Remove Filament From Extruder (Don't want to cook it)
	 * Bring heat bed up to operating temp (ABS = 105c, PLA = 60c)
     * Bring extruder up to operating temp (PLA = 210)

2. Zero out offset (temporarily)

         M851 Z0 

3. Wait for heated bed to come up to temp
4. Get Z probe trigger distance
    1. Run `G28` to home Z
    2. Descend to Z0 location and add probe X offset `G0 Z0` ( In our case probe is 25mm left of nozzle so X = X - 25, Use M114 to get current X)
    3. Place piece of paper under extruder (old inst was to use 0.063 feeler gauge)
    4. Descend in 0.1mm increments while moving paper back and forth waiting until you feel it pinch (noticeable grab)
    5. Record Z offset
            
            M114
         Ex. -0.50
    6.  This number represents the distance *below* the nozzle tip that the sensor triggered
5. Calculate z offest + fudge factor of -0.08??.  (Ex -0.30 + -0.08 = -0.38)
6. Calculate z offest + thickness of paper -0.1  (Ex -0.50 + -0.10 = -0.60)
    the more negative the closer the extruder is to the build plate 
    Note: We do the negative because the probe is triggering below the nozzle tip (Always the case with a static probe)
7. Temporarily set the new z offset

         M851 Z-0.40
         SENDING:M851 Z-0.40
         echo:Z Offset -0.40

8. Home all

        G28
9. Descend to .1mm

        G0 Z0.1

10. Test with paper (or if you're fancy use feeler gauge .102mm)
     Note: you should feel it drag but not be completely pinched (for feeler gauge .102mm should feel drag but 0.076 should be free.
     
      
12. 
13. Run a test print (Something with a big flat bottom surface)
14. Cancel after the 1st layer is put down (Or sooner if it's obviously not going to stick)
15. Raize Z by 10mm (To get your extruder out of the way)
16. Set the bed temp to your preset (So you'll be ready for the next run
17. Remove the 1st layer and inspect the bottom 
   * You should have COMPLETE coverage on the 1st layer no gaps
   * Layer should be completely fused (doesn't separate along extrusion lines when pulled)
   * It's better to over be a little over extruded on the 1st layer then under extruded
 12. If the above failed add a correction of -0.05 (For our example -0.40 + -0.05 = -0.45)
 
          M851 Z-0.45
18. Repeat the test and add corrections until it passes
19. Save offset to firmware
    1. Open Anduino IDE
    2. Edit configure.h
 
            Z_PROBE_OFFSET_FROM_EXTRUDER = -0.45
        Note: You can get the current offset by running `M851` without any arguments 
    3.  Save and upload (DON'T forget to disconnect PRONTERFACE from the serial first
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzI0MjI3MjAxLDE0Mjg1MDY4OTEsLTE3Mj
kwODEzMTgsLTM0OTkzOTI5Miw1NDQ1NDQ3ODVdfQ==
-->