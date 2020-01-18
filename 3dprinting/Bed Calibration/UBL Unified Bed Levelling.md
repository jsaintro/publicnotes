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

3. Save to eeprom

        M500

 3. Current eeprom settings
 
        M501
         
 5. Preheat bed and hotend
	 *PLA*
	```	 
	M140 S65
	M104 S215
	```
	*ABS*
	```	 
	M140 S100
	M104 S255
	```
	
4. Probe bed
    ```
    G28
    G29 P1 V3
    ```
    Note: 
5. Check out the output
    ```
    G29 T
    ```
6. Save Mesh
    ```
    G29 S1 // S1 for PLA S2 for ABS
    ```
8. Set Fade height
    ```
    G29 F10.0
    ```
     Gradually fade out the compensation by 10mm  
9. Activate the UBL
  G29 A
  10. Save the settings
   M500

# Set probe offset
1. Clear current
M851 Z0
2. Home and center
G28 
3. Disable software endstops
M211 S0
4. Adjust down till you touch paper
5. See setting
M114
That's your offset Z-0.71 Z-2.56
6. Set in firmware
#define Z_PROBE_OFFSET_FROM_EXTRUDER -0.71
7. Do in terminal
M851 Z-0.71
M500 //to save
8. Run mesh validation print
G28
G26 P5 //P10 primes with 10 mm of filament
9. Resave
 G29 S1
 M500
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
G29 L1 // Load mesh one
G29 J

```
Bed Topography Report:
    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.116  +0.212  +0.309  +0.366  +0.440  +0.477  +0.517  +0.580    .
   |
 7 |   .     +0.010  +0.097  +0.178  +0.259  +0.334  +0.375  +0.431  +0.487    .
   |
 6 |   .     -0.101  -0.046  +0.060  +0.125  +0.207  +0.292  +0.352  +0.405    .
   |
 5 |   .     -0.216  -0.150  -0.068  +0.004  +0.097  +0.169  +0.245  +0.300    .
   |
 4 |   .     -0.315  -0.261 [-0.155] -0.100  -0.011  +0.075  +0.142  +0.215    .
   |
 3 |   .     -0.405  -0.338  -0.253  -0.181  -0.093  -0.011  +0.057  +0.110    .
   |
 2 |   .     -0.456  -0.388  -0.293  -0.221  -0.138  -0.070  -0.003  +0.030    .
   |
 1 |   .     -0.564  -0.469  -0.366  -0.293  -0.221  -0.168  -0.141  -0.097    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)
Bed Topography Report:
    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.028  +0.119  +0.229  +0.290  +0.349  +0.389  +0.447  +0.512    .
   |
 7 |   .     -0.057  +0.035  +0.125  +0.190  +0.254  +0.304  +0.360  +0.415    .
   |
 6 |   .     -0.158  -0.053  +0.037  +0.094  +0.149  +0.218  +0.260  +0.329    .
   |
 5 |   .     -0.251  -0.163  -0.070  -0.011  +0.062  +0.110  +0.172  +0.227    .
   |
 4 |   .     -0.343  -0.260 [-0.151] -0.091  -0.037  +0.019  +0.065  +0.132    .
   |
 3 |   .     -0.463  -0.363  -0.260  -0.190  -0.141  -0.086  -0.021  +0.035    .
   |
 2 |   .     -0.519  -0.453  -0.335  -0.278  -0.213  -0.156  -0.078  -0.041    .
   |
 1 |   .     -0.636  -0.536  -0.438  -0.363  -0.305  -0.259  -0.208  -0.171    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)
```  
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3NjgxOTg3NiwxMTU4MzcxODYwLC0xMD
czNDk1NjcyLDI3NDIwNTYxNywxMTQ3Njg5MTEwLDQ4MjUyNDMz
Ml19
-->