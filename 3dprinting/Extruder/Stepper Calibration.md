
# Calibrate Steps per MM
1. Tools Needed
	* Metric Ruler
	* Sharp Sharpie Ultra Fine Point
2. Print Diagnostic print[https://www.thingiverse.com/thing:2975429/](https://www.thingiverse.com/thing:2975429/)
3. **Resolution:**
30% infill
0.1 lh
thin walls

**Infill:**

30%
4. Disable Filament Sensor
5. Measure 120mm on fliament from extruder entry point (Doesn't have to be exact, just consistent) and mark filament with sharpie
6. Heat filament to 215 (Natural RS)
7. Extrude 100mm
    ```
    G91
    G1 E100 F100
   ```
8. Measure filament mark (From same spot)
    20mm.
    120mm(1st measurement) - 20mm(2nd mesurement) = 100 (measured distance)
9. Retrieve number of esteps
	6. M503
	7. Look for M92
	8.  EXXX where xx is steps for MM
10. Calculate correction
	Desired distance / measured distance * Current e steps = new e steps
11. Temporarliy set new esteps
12. M92 E{{ New E Steps}}
13. 
14. Enable filament Sensor
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMjQ0NzAxNCwxMDgyMjY0MzMwLDEyMz
gzNTQwODYsMjA0NzkyODk5NSwtMjUxNTMwNzkwLDQ5NzgxODgx
MF19
-->