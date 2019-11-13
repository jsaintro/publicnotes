
# Calibrate Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie Ultra Fine Point
2. Disable Filament Sensor
3. Measure 120mm on fliament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
4. Heat filament to 215 (Natural RS)
5. Extrude 100mm
    ```
    G91
    G1 E100 F100
   ```
7. Measure filament mark
8. Retrieve number of esteps
	6. M503
	7. Look for M92
	8.  EXX where xx is steps for MM
9. Calculate correction
	Desired distance / measured distance * Current e steps = new e steps
10. Temporarliy set new esteps
11. M92 E{{ New E Steps}}
12. 
13. Enable filament Sensor
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNTQ4NjI5ODYsMTIzODM1NDA4NiwyMD
Q3OTI4OTk1LC0yNTE1MzA3OTAsNDk3ODE4ODEwXX0=
-->