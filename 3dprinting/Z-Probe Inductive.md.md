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
1. Lower extruder till it is almost touching bed ~.5 - 1mm
2. Use paper to figure out max trigger distance
3. Remove a couple of slips of paper and faster there

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
```
#define min_software_endstops false
```
## Better Directions
1. Flash marlin with 1 offset
    1. Open Anduino IDE
    2. Edit configure.h
 
            Z_PROBE_OFFSET_FROM_EXTRUDER = 0
    3.  Save and upload
        
2. Preheat bed to operating temp (ABS = 100c PLA = 60c?) ## EXPERIMENTAL
3. Get Z probe trigger distance
    1. Run `G28` to home Z
    2. Descend to Z0 location `G0 Z0`
4. Descent to 1st layer distance
     1. Place 0.063 feeler guage under extruder
     2. descent in .1 increments while moving the feeler back and forth waiting until you feel it pinch
     3.  Record Z for M114 (Ex. -0.40)
5.  This number represents the distance *below* the nozzle tip that the sensor triggered
6. Set Z_PROBE_OFFSET_FROM_EXTRUDER to negative value of the distance Ex. Distance = 0.40 = -0.40 Z_PROBE_OFFSET
    Note: We do the negative because the probe is triggering below the nozzle tip (Always the case with a static probe)
7. Test
    Use a simple test print and see if 1st layer is going town (No gaps between lines and not peeling up in spots
8.  Fine tune: If it's still not perfect add another 0.1 so for our example that would be -0.50

## Delete rest once you get above directions working

Re-calibrate current z Position to 10mm (So we can move down 10mm from current)
```
G92Z10
```


9. Move z down in .1mm increments until .051mm feeler is pinched then backoff .1
10. Determined current position
```
M114
```
Z1 = 9.16
9.16 - 10 = -.84 -1.02 -1.12 -1.15 -5.5=4.53 -4=3.53
Z= 9.70 - 10 = -0.3
Z2 = -1.80
-0.3 + -1.80 = -2.1

Since trigger is closer than hotend

-1.26
Offset from ext
Negative means closer to min endstop. pos means further from min endstop

 calibrate current position to 10mm off bed surface (So we can move below)
Move Z down in .1mm increments until hotend just touches feeler guage .7??
Save in Z_PROBE_OFFSET_FROM_EXTRUDER

# Repeatability
```
ok
Bed x: 25.00 y: 20.00 z: -0.83
Bed x: 92.00 y: 20.00 z: -0.93
Bed x: 159.00 y: 20.00 z: -0.83
Bed x: 160.00 y: 92.00 z: -0.81
Bed x: 93.00 y: 92.00 z: -0.92
Bed x: 26.00 y: 92.00 z: -0.83
Bed x: 25.00 y: 164.00 z: -0.77
Bed x: 92.00 y: 164.00 z: -0.92
Bed x: 159.00 y: 164.00 z: -0.82
Eqn coefficients: a: -0.00 b: 0.00 d: -0.86
planeNormal x: 0.00 y: -0.00 z: 1.00
ok
echo:endstops hit:  Z:-0.82
echo:Home X/Y before Z
ok
ok
echo:Home X/Y before Z
ok
ok
Bed x: 25.00 y: 20.00 z: -0.84
Bed x: 92.00 y: 20.00 z: -0.96
Bed x: 159.00 y: 20.00 z: -0.86
Bed x: 160.00 y: 92.00 z: -0.81
Bed x: 93.00 y: 92.00 z: -0.92
Bed x: 26.00 y: 92.00 z: -0.80
Bed x: 25.00 y: 164.00 z: -0.74
Bed x: 92.00 y: 164.00 z: -0.89
Bed x: 159.00 y: 164.00 z: -0.82
Eqn coefficients: a: -0.00 b: 0.00 d: -0.86
planeNormal x: 0.00 y: -0.00 z: 1.00
ok
echo:endstops hit:  Z:-0.82
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDY2NTU0MjQsLTE5MDI0MzQ0MjAsNT
g3MTUxMjI4XX0=
-->