
# Calibrate Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie
2. Measure 120mm on fliament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
3. Extrude 100mm
	G1 E100 F100
4. Measure filament mark
5. Retrieve number of esteps
	6. M503
	7. Look for M92
	8.  EXX where xx is steps for MM
6. Calculate correction
	Desired distance / measured distance * Current e steps = new e steps
7. Temporarliy set new esteps
8. M92 E{{ New E Steps}}
9. 
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI1MTUzMDc5MCw0OTc4MTg4MTBdfQ==
-->