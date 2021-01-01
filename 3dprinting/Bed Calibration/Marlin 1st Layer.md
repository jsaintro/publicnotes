
# Marlin 1st Layer

## Prerequisites
1. UBL Unfied Bed Levelling procedure has been done for PLA
2. Generate gcode from [here](https://teachingtechyt.github.io/calibration.html#firstlayer)
    |Setting|Value|Value 2|
    |--|--|--|
    |Additional start gcode|Check|G29 L2<br/>G29 A|
    |Bed X dimension (mm)|220||
    |Bed Y dimension (mm)|208||
    |Extra margin from edge (mm)|8||
    |Hot end temperature (deg C)|230||
    |Bed temperature (deg C)|85||
    |Audo Bed Levelling|No ABL||
    Note: L2 is the mesh to load (L1 = PLA/L2 = PETG/L3 = ABS)
3. Do the test print
    * If it's not sticking baby step closer to the bed
    * If you see ridges baby step further from the bed
    * If the pads aren't consistent look at the mesh bed leveling
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NTExMjAwODUsLTE1OTMyMDkyODMsMT
g4NzE1NjkyOCwtMTIxNzkyMDY2MywtNzA2MzM1Njk1LDkzNzc3
NTE1NCwtMTYyMzE2NTYzOF19
-->