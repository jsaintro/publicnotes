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
  M140 S60
  M104 S210
3. Probe bed
    ```
    G28
    G29 P1 V3
    ```
4. Check out the output
    ```
    G29 T
    ```
6. Save Mesh
 G29 S1
 8. Set Fade height
  G29 F 10.0 (Start leveling off the mesh buy 10mm
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
8. Run mesh validation print
G28
G26 P5 //P10 primes with 10 mm of filament
9. Resave
 G29 S1
 M500
 10. Tuning the bed 
 11. [https://www.youtube.com/watch?v=ONpKxkil16Q](https://www.youtube.com/watch?v=ONpKxkil16Q) 13.58
 12.  
# Loading a mesh
G29 L2 // to load 2nd slot
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwOTU0NzM5MTcsMjIwOTI1Nzg5LDE0ND
Q4MjQ3NTUsLTEzODE5MjcwNjUsLTE5MTE0MTU3ODksMTUyNDEx
Mjk0MSwtMTM5NDMwNzkxMSwxODA2OTMwMjI0LC0xNDg3ODIyNz
c3LDEzODk5NDMyMzUsODM0MjA0Mjk2LC0xMjM2ODM5MTg0LC05
NzU4MTMxNzJdfQ==
-->