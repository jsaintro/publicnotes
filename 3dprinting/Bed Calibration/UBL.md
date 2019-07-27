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
4. G29 P1
5. Check out the output
  G29 T
7. Save Mesh
 G29 S1
 8. Set Fade height
  G29 F 10.0 (Start leveling off the mesh buy 10mm
  9. Activate the UBL
  G29 A
  10. Save the settings
   M500
# Set probe offset
1. Home and center
G28 
2. Disable software endstops
M211 S0
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzM3NjM1NjQsMTgwNjkzMDIyNCwtMT
Q4NzgyMjc3NywxMzg5OTQzMjM1LDgzNDIwNDI5NiwtMTIzNjgz
OTE4NCwtOTc1ODEzMTcyXX0=
-->