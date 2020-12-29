# Config
```
#define AUTO_BED_LEVELING_UBL

#define RESTORE_LEVELING_AFTER_G28

#define MESH_INSET (abs(X_PROBE_OFFSET_FROM_EXTRUDER) - 10)

#define MESH_EDIT_GFX_OVERLAY   // Display a graphics overlay while editing the mesh
#define G26_MESH_VALIDATION
#define EEPROM_SETTINGS // Enable for M500 and M501 commands
```

# Operation
1. Reset to defaults

        M502

2. Save to eeprom

        M500

 3. Current eeprom settings
 
        M501
         
 4. Preheat bed and hotend
     Note: Wait for the bed to come up to temp before starting on the hot end. No reason to cook plastic. Also if possible remove the filament before doing this.
     
	 *PLA*
	```	 
	M140 S65 ; heat up the bed
	M104 S190 ; heat up the hot end
	```
	*ABS*
	```	 
	M140 S100 ; heat up the bed
	M104 S255 ; heat up the hot end
	```
	
3. Probe bed
    ```
    G28 ; Home Z
    G29 P1; Probe the bed 
    ```
    Note: 
4. Check out the output `.` are spots that will need to be interpolated
    ```
    G29 T
    ```
    Note: Any points listed with a `.` are probably outside the probe limits and ___must___ be interpolated
5. Interpolate missing border points (Note this isn't great for edges, Consider tweaking bed dimensions to remove the need for this)

	```
	G29 P3 T
	G29 T
	```
	Note: repeat all points are interpolated
	
6. Save Mesh
    ```
    G29 S1 // S1 for PLA S2 for ABS
    ```
7. Set Fade height
    ```
    G29 F10.0
    ```
     Gradually fade out the compensation by 10mm  
8. Activate the UBL
    ```
    G29 A
    ```
9. Save the settings
    ```
    M500
    ```

# Set probe offset
1. Clear current
    ```
    M851 Z0
    ```

2. Home and center
    ```
    G28
    ``` 

3. Disable software endstops
    ```
    M211 S0
    ```

4. Adjust down till you touch paper
5. See setting
    ```
    M114
    ```
    Note: That's your offset Z-0.71 Z-2.56 Z-1.0

6. Set in firmware
    ```
    #define Z_PROBE_OFFSET_FROM_EXTRUDER -0.71
    ```
    
7. Do in terminal
   ```
    M851 Z-0.71
    M500 //to save
    ```
    
8. Run mesh validation print
    ```
    G28
    G26 I0 P2 //P2 primes with 2 mm of filament using PLA settings??
    ```
    
9. Resave
    ```
    G29 S1
    M500
    ```
    
 # Fine Tuning Mesh
 Use LCD go into mesh edit
 scroll to point and adjust using paper
 Will 
 will automat Tuning the bed
  
 12. [https://www.youtube.com/watch?v=ONpKxkil16Q](https://www.youtube.com/watch?v=ONpKxkil16Q) 13.58
 13.  
 1
# Loading a mesh
G29 L2 // to load 2nd slot

# Pre Print Mesh Tilt
NOTE: This currently sucks so just fix the bed in place and don't bother.
G29 L1 // Load mesh one
G29 J

### Troubleshooting
[https://github.com/MarlinFirmware/Marlin/issues/7508](https://github.com/MarlinFirmware/Marlin/issues/7508)
[http://marlinfw.org/docs/gcode/G029-ubl.html](http://marlinfw.org/docs/gcode/G029-ubl.html)

```

# Perfect Mesh
1. Try and get all points probed
	2. Set bed dimensions to actual bed dimensions
	3. 
	4. If probe offset is less than calculated mesh probe point it won't probe that point. (Play with  
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDc2NzA0Nzg2LC0xNTQ4ODkyNjYxLDE0Mj
I1MjcxOTIsLTE0MTM0NjY1OTUsLTE1NzExMzU2NjAsLTEzNzA5
OTIzMTQsLTE2NTc5Mzk2NSwxMzA5NzQ2NTIwLDEyMDQ1MDA0MT
ksODQwNjIxMzIyLC03NzcwNzk3NzcsMTE3NzY5MTc5MywyNDIx
MzM4OSwxNTUwMDMxNjI5LC0xNDMwNDgxOTM5LDEwMDUyMzY5Nz
MsNTM0MzQ2NTUyLDE1NDY1OTY4NzMsLTQ2MzczNDk2NSwyMDI4
MTcxNjU5XX0=
-->