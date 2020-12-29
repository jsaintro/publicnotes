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

# Perfect Mesh
1. Try and get all points probed
2. Set bed dimensions to actual bed dimensions
    ```
    #define  X_BED_SIZE  220
    #define  Y_BED_SIZE  208
    ```
3. Set Travel Limits
    ```
    #define  X_MIN_POS  -16 // X End stop is 16mm past X=0
    #define  Y_MIN_POS  -3 // Y End stop is 3mm past Y=0
    #define  Z_MIN_POS  0 // Going through the bed with the hotend is never a good idea ;-)
    #define  X_MAX_POS  X_BED_SIZE
    #define  Y_MAX_POS  Y_BED_SIZE
    #define  Z_MAX_POS  220
    ```
	5. Make sure probe offset is exactly right
	    ```
	    #define  NOZZLE_TO_PROBE_OFFSET { 23, 5, -1.3 } // My probe is 23mm X, 5mm Y, and 1.3 Higher than Z
	    ```
	6. To calculate your mesh border probe point must be within travel limits of nozzle + probe offsets.
	7. Ex. My probe is 23mm offset from nozzle. NozzeX/Y Probe offsets + Mesh border needs to be within travel limits for it to be able to probe all points
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MzY0MjYzNTIsLTE1NDg4OTI2NjEsMT
QyMjUyNzE5MiwtMTQxMzQ2NjU5NSwtMTU3MTEzNTY2MCwtMTM3
MDk5MjMxNCwtMTY1NzkzOTY1LDEzMDk3NDY1MjAsMTIwNDUwMD
QxOSw4NDA2MjEzMjIsLTc3NzA3OTc3NywxMTc3NjkxNzkzLDI0
MjEzMzg5LDE1NTAwMzE2MjksLTE0MzA0ODE5MzksMTAwNTIzNj
k3Myw1MzQzNDY1NTIsMTU0NjU5Njg3MywtNDYzNzM0OTY1LDIw
MjgxNzE2NTldfQ==
-->