
# Calibrate Extruder Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie Ultra Fine Point
2. Print Diagnostic print[https://www.thingiverse.com/thing:2975429/](https://www.thingiverse.com/thing:2975429/)
	* layer height: 0.1
	* infill: 30%
    * Detect thin walls
3. Disable Filament Sensor
4. Measure 120mm on filiament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
5. Heat filament to 215 (Natural RS)
6. Extrude 100mm
    ```
    M104 S215
    G91
    G1 E100 F100
   ```
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
10. Make the change permanent in the slicker settings
     Add this area in from XYZ calibration 
12. Enable filament Sensor
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ1NDcwNzA0NCwxODQ2NzQ3NjkzLC0xOT
I3NTAxMTg3LDg1NTM2OTgyMF19
-->