
# Calibrate Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie Ultra Fine Point
2. Print Diagnostic print[https://www.thingiverse.com/thing:2975429/](https://www.thingiverse.com/thing:2975429/)
3. Disable Filament Sensor
4. Measure 120mm on fliament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
5. Heat filament to 215 (Natural RS)
6. Extrude 100mm
    ```
    G91
    G1 E100 F100
   ```
7. Measure filament mark (From same spot)
    20mm.
    120mm(1st measurement) - 20mm(2nd mesurement) = 100 (measured distance)
8. Retrieve number of esteps
	6. M503
	7. Look for M92
	8.  EXXX where xx is steps for MM
9. Calculate correction
	Desired distance / measured distance * Current e steps = new e steps
10. Temporarliy set new esteps
11. M92 E{{ New E Steps}}
12. 
13. Enable filament Sensor
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA4MjI2NDMzMCwxMjM4MzU0MDg2LDIwND
c5Mjg5OTUsLTI1MTUzMDc5MCw0OTc4MTg4MTBdfQ==
-->