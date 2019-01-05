
# Stats
* Weight ??g
* LJ12A3-4-Z/BX
* DC 6V-36V M? 4mm NPN NO LJ8A3-2-Z/BX-5V Inductive Proximity Sensor Switch
# Wiring
Blue = Ground
Brown = 12V
Black = Schottky Diode (BAT85) Neg Terminal (Black Band)
Schottky Diode (BAT85) Pos Terminal = Arduino Z Stop Normally Open Pin (With pullup)

# Schottky Diode Magic
When the sensor is open aka high the Schottky diode is reverse biased and no current flows to sense pin.  So the pullup of the sense pin makes it a logic high.  When the sensor is triggered the sensor goes to ground causing a forward bias of the diode.  This effectively lets the diode flow to ground which causes a logic low on the arduino.  



# Surface Notes

NOTE: Need to verify with the 4mm probe
With 3mm alu bed has about a 2mm detection distance.  So PEI sheet must be very thin

# Mechanical Placement
1. Double paper over and place under extruder
2. Lower extruder till it touches paper in 0.1mm increments
3. Raise extruder .1mm
4. See if sensor has triggered with M119 (Z endtop triggered)
5. If not then rotate sensor 1/4 and check M119 repeat till triggered
6. Repeat steps 1 till sensor triggers
7. Remove a couple of slips of paper and faster there

# Accuracy Test
Enable M48 in firmware `#define Z_MIN_PROBE_REPEATABILITY_TEST`

Run the repeatability test

        G28
        M48 P10 X100 Y100 V2 E L2
P = Number of times
X/Y = x/y positon
V = verbosity 1-4
E = Engage probe after each reading
L = Legs of movement?
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

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY1Njc4NjE2OCwtMTM2NTY2ODEwN119
-->