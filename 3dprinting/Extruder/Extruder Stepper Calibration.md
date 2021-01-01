
# Calibrate Extruder Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie Ultra Fine Point
2. Print Diagnostic print[https://www.thingiverse.com/thing:2975429/](https://www.thingiverse.com/thing:2975429/)
	* layer height: 0.1
	* infill: 30%
    * Detect thin walls
3. Disable Filament Sensor (If you have one)
4. Measure 120mm on filiament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
5. Heat filament 10 degrees higher than normal 200 (PLA) 250 (PETG) 260? ABS?
6. Extrude 100mm
    ```
    M104 S215
    G91
    G1 E100 F50
   ```
   Note: If G91 doesn't seem to work so just run G92 E0 to reset extruder to 0 if you want to redo
7. Measure filament mark (From same spot)
    Desired distance / measured distance * Current e steps = new e steps
    120mm(1st measurement) - 20mm(2nd measurement) = 100 (measured distance)
8. Retrieve number of esteps
    ```
    M503
        ```
	Look for M92
	EXXX where xx is steps for MM
9. Temporarliy set new esteps
```
    M92 E{{ New E Steps}}
```
Ex. `M92 E100`

10. Set in slicer printer gcode for this filament type
```
{elsif filament_notes[0]=~/.*RS_BLACK_PLA.*/}
M92 X100.46 Y100.41 Z398.58 E280.00 ; fine tune steps per mm JSR
{endif}
```
11. Also add a note in the filament notes section for the slicer saying you've done this calibration for this filament
12. E steps calibrated
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3ODQ3MzY0OCwtMzQ4NjEwODg2LC02MD
Y5MDg0ODIsNjIyMTQ3NzMyLC00NDM5OTQ1ODEsODA1NDM4MzMz
LC0xODg0MTE2NTQsLTQ1NDcwNzA0NCwxODQ2NzQ3NjkzLC0xOT
I3NTAxMTg3LDg1NTM2OTgyMF19
-->