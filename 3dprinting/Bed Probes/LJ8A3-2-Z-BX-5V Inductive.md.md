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
4. Verify that has triggered with M119 (Z endtop triggered)
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
    Metal pliers under sensor etc...
    ```
    Reporting endstop status
    x_min: open
    y_min: open
    z_min: TRIGGERED
    ok
    ```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzAyNjY5NTA3LDcyNDIyNzIwMSwxNDI4NT
A2ODkxLC0xNzI5MDgxMzE4LC0zNDk5MzkyOTIsNTQ0NTQ0Nzg1
XX0=
-->