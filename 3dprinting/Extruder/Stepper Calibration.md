
# Calibrate Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie 
2. Measure 120mm on fliament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
3. Heat filament to 215 (Natural RS)
4. Extrude 100mm
	G1 E100 F100
5. Measure filament mark
6. Retrieve number of esteps
	6. M503
	7. Look for M92
	8.  EXX where xx is steps for MM
7. Calculate correction
	Desired distance / measured distance * Current e steps = new e steps
8. Temporarliy set new esteps
9. M92 E{{ New E Steps}}
10. 
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNDE3OTkzNywyMDQ3OTI4OTk1LC0yNT
E1MzA3OTAsNDk3ODE4ODEwXX0=
-->