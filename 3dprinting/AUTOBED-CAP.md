# Stats
* Weight 57g
* LJC18A3-H-Z/BX
* NPN 6-36V/300mA 1mm - 10mm NO

# Wiring
Blue = Ground
Brown = 12V
Black = Schottky Diode (BAT85) Neg Terminal (Black Band)
Schottky Diode (BAT85) Pos Terminal = Arduino Z Stop Normally Open Pin (With pullup)

# Schottky Diode Magic
When the sensor is open aka high the Schottky diode is reverse biased and no current flows to sense pin.  So the pullup of the sense pin makes it a logic high.  When the sensor is triggered the sensor goes to ground causing a forward bias of the diode.  This effectively lets the diode flow to ground which causes a logic low on the arduino.  

# Adjustment
CCW More sensitive
CW Less Sensitive
# Will this cook my arduino?
* Shouldn't.. when untriggered the sense pin is floating
  When you measure it using a multimeter it will show 12v becuase it's an induced current.  Using the pullup on the arduino sense pin will keep it from floating and it will read 5v when untriggered.  When triggered it will go to ground.

# How well will this work on my surface??
1. Mirrored Glass is best
* This is a CAPACITIVE SENSOR so it's basically measuring the distance between two conductors.  Glass is an insulator so bare glass means that you'll be measuring the distance between the sensor and what's under the glass ... the heatbed (Prone to error/warping non uniform conductance.  But a mirror is ideal because a modern mirror is a piece of glass with a thin layer of conductive metal (Which is very uniform ;-).  If you check the back of a mirror for conductivity keep in mind that they normally put a layer of non-conductive paint to protect the metal from corrosion.
* Recommended distance 2 - 4 mm
* If it's too close you run the risk of triggering off the something below the sensor.  Too far and you increate your target area which reduced your accuracy.

* Arduino pin with pullup installed and unattached
  Sense Pullup V 4.897 Vcc 4.921
* with Sendor attached Same as Pullup

* Unattached 9.90 V


* Signal light glows slightly when hooked up to sense pin. (If diode isn't working)
* 33 Ohm current limiting resistor didn't help
* 50% voltage divider didn't help 
  10K/10K 4.8V when open 1V when grounded.

# Mechanical Placement
1. Lower extruder till it is almost touching bed ~.5 - 1mm
2. Move so that sensor is above a binder clip
3. Adjust sensor so it doesn't hit binder clip

# Test sensor functionality
1. With sensor untriggered (faint light)
    Send M119 to see if Z endstop is untriggered
    ```
    Reporting endstop status
    x_min: open
    y_min: open
    z_min: open
    ok
    ```

2. Trigger sensor (Strong light)
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
1. Preheat hotend and preheat bed
1. Calibrate with top 
G0 Z150
G92Z100
G0 Z170 (increase till you hit top)
G0 Z100

1. Home Z/Autobed Calib/Pos Extruder
```
G28
G29
G0 X150 F7000
```

1. Determine current percieved z pos
```
M114
X:150.00 Y:164.00 **Z:9.02** E:-300.00 Count X: 12000 Y:13120 Z:35569

READ: X:150.00 Y:164.00 Z:4.84 E:0.00 Count X: 12000 Y:13120 Z:21173
```

1. Slowly lower to the bed Until tip is .06mm away via feeler guage
1. Determine current percieved z pos
```
M114
X:150.00 Y:164.00 **Z:3.52** E:-300.00 Count X: 12000 Y:13120 Z:35569
```
READ: X:150.00 Y:164.00 Z:-1.56 E:0.00 Count X: 12000 Y:13120 Z:-4011

1. Add current z number to current offset
Ex. -4 + 3.52 = -.48
1. Set as z offset
1. repeat above steps (Calibrate unitl it reads same as feeler guage)
-.48 + .3 = -.45

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
    2. descent in .1 increments till you f 
 4. Use .076 feeler or piece of paper and place under nozzle
 5. Move down .1 increments till you feel friction between nozzle tip and feeler
6.  Back off .1 (Exp1 didn't do this
7.  Record Z for M114 (Ex. -3.00) Ex Z:-0.40
8.  Take difference of these 2 measurements (Ex. -2.70 - -3.00 = 0.30) Ex. 0 - -0.40 
9.  This number represents the distance *below* the nozzle tip that the sensor triggered
10. Set Z_PROBE_OFFSET_FROM_EXTRUDER to negative value of the distance Ex. Distance = 0.30 = -0.30 Z_PROBE_OFFSET
    Note: We do the negative because the probe is triggering below the nozzle tip (Always the case with a static probe)

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
eyJoaXN0b3J5IjpbLTEyNjcwNTE4MTgsMTQ2Mjk4OTc5MiwtMT
YzNzU3ODI5MiwyNTIyNTE5MjIsLTExNDY5NDIxOSw4MDEzODIz
NDksLTYwNjU4MDc3NSwtMzE4MzcwOTk0LC0xOTM4MDA3Mzk5LC
01MDA5NDUyNzQsNjQ5NTg0NjYyLDE1OTEzNDk4OTIsLTU0NzAz
NzcyLC0xOTc2NTg1OTA2LDE0MTA2Njg0MjVdfQ==
-->