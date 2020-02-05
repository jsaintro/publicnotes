
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
Ex. `M92 E100`

10. Update in firmware
   Add firmware line here!!!
11. Flash firmware
12. Reset NVRAM
```
M502
M500
```
Note: Flashing doesn't remove this setting that's why you have to do it twice

14. Make the change permanent in the slicker settings
     Add this area in from XYZ calibration 

15. Enable filament Sensor (If you have one)
	
<!--stackedit_data:
eyJoaXN0b3J5IjpbODA1NDM4MzMzLC0xODg0MTE2NTQsLTQ1ND
cwNzA0NCwxODQ2NzQ3NjkzLC0xOTI3NTAxMTg3LDg1NTM2OTgy
MF19
-->