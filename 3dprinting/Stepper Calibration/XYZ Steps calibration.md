



# Calibrate XYZ Steps per MM
1. Tools Needed
	* Digital Calipers
	* Sharp Sharpie Ultra Fine Point
2. Get the current Steps
```
M503
Recv: echo: M92 X100.00 Y100.00 Z400.00 E280.00
```
Note look for the M92 line those are your steps per mm

3. Print this object with the following settings
	 [https://www.thingiverse.com/thing:195604](https://www.thingiverse.com/thing:195604)

		* 10% infill grid
		* .2mm layer height
		* .2mm Speed MK3 profile
		* 2 shells

4. Once done label the X and Y axes on the print (So you don't loose them once you remove the part
5. Measure x and y with digital calipers 
	X = 99.35 Y = 99.59
6. Measure z with digital calipers
    Measure from top to upper surface of x or y arm (ideal is 45mm)
    Note: this is done because 1st layer can be inconsistent.
8. Calculate the correction factor
	X,Y-Axis: 100mm / [measured length in mm] _[current STEPS]  
	Z-Axis: 45mm / [measured height in mm]_ [current STEPS]
	Ex.
	  X: 100/ 99.35 * 100 = 100.65
	  Y: 100/99.59 * 100 = 100.41
	  Z: 45/45.16 * 400 = 398.58
9. Update slicer start gcode with steps line
    ```    
    {if filament_notes[0]=~/.*RS_NAT_PLA.*/}
    M92 X100.65 Y100.41 Z398.58 E280.00 ; fine tune steps per mm JSR
    {endif}
    ```
Note: In the `Notes` for the filament you must have the filament name.  In this example it's `RS_NAT_PLA`
Note: [Nifty macro language reference](https://github.com/prusa3d/PrusaSlicer/wiki/Slic3r-Prusa-Edition-Macro-Language) 
## Alt
 2. Print this
	 [https://www.thingiverse.com/thing:2050876](https://www.thingiverse.com/thing:2050876)
	 or this
Follow the steps below to calibration your X and Y axis:  
1.Connect to your printer via a USB connection (direct to computer or Octoprint, etc.)

1.  Issue the M503 command
2.  Scroll back through the output of the M503 command and look for the M92 output. Mine was  `M92:X100.00 Y100.00 Z400.00 E161.30`. Copy down these numbers. The M92 command sets the numbers of steps the stepper motors will move based on movement instructions in your GCODE
3.  Download, slice, and print the calibration square included with this Thing
4.  Before removing the square from the bed, note that the X-axis is left to right movement and Y axis is front to rear movement.
5.  Using calipers, measure the distance across the X-axis in at least three places. I suggest measuring 10mm from each end, plus once in the middle. Write down these distances.
6.  Average the three distances. Write down this average for the X-axis. Mine was 99.79.
7.  Using calipers, measure the distance across the Y-axis in at least three places. I suggest measuring 10mm from each end, plus once in the middle. Write down these distances.
8.  Average the three distances. Write down this average for the Y-axis. Mine was 99.63.
9.  Next, use this formula to determine new M92 values:  
    New M92 value = Desired movement / Actual movement * Current M92 value
    
    **So for example,**
    
    **New M92 for X (100.21) = 100/99.79*100**
    
    **So for example,**
    
    **New M92 for Y (100.37) = 100/99.63*100**
    
10.  Create the new M92 command by replacing the X and Y values above with the new calculated values:  
    `M92 X100.21 Y100.37 Z400.00 E161.30`
11.  This changed code can be activated in two ways. The easiest is to enter the new command while connected to the printer via USB from your computer, then enter M500 to save the value. You can confirm the new value was stored by entering M503 and looking for the updated M92 line in the config. The other option is to change this line of code in the startup GCODE in your slicer profiles. To do this, place this line in the Startup GCODE in your slicer. In Simplify3D this is placed in the Scripts --> Starting Scrip area. In Slic3r this is in Printer Settings --> Custom G-code.
12.  Re-slice the Calibration square
13.  Re-print the Calibration square
14.  Mark and measure the new calibration square as in steps 5-8 above
15.  Average the distances for X and Y These should now be closer to 100.0mm
16.  If you are satisfied with the results, you are done! If the distances are not as close to 100mm as you desire, if not happy with results, repeat the calibration process.

Note that this test was done with PLA. When you change material, you should re-test dimensions, and may need to re-calibrate your M92 values.

If you want to adjust your Z or E axis, please refer to the Instructables article.

[http://www.instructables.com/id/Calibrating-your-3D-printer-using-minimal-filament/](http://www.instructables.com/id/Calibrating-your-3D-printer-using-minimal-filament/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ1MTE5ODExMl19
-->