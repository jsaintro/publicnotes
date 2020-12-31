
# Marlin 1st Layer

## Prerequisites
1. UBL Unfied Bed Levelling procedure has been done for PLA
2. Generate gcode from [here](https://teachingtechyt.github.io/calibration.html#firstlayer)
    |Setting|Value|Value 2|
    |--|--|--|
    |Additional start gcode|Check|G29 L2<br/>G29 A|
    |Bed X dimension (mm)|220||
    |Bed Y dimension (mm)|208
    Note: L2 is the mesh to load (L1 = PLA/L2 = PETG/L3 = ABS)
	2. [https://www.thingiverse.com/thing:3730866](https://www.thingiverse.com/thing:3730866)
	3. Search for and set the correct temperatures 
```
M104 Sxxx; set hotend temp to xxx  
M140 Syyy; set bed temp to yyy  
M190 Syyy; wait bed temp  
M109 Sxxx; wait hotend temp
```
2
4. Select "Change Filament" From menu and load PLA
5. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1MjE0MzM0LDE4ODcxNTY5MjgsLTEyMT
c5MjA2NjMsLTcwNjMzNTY5NSw5Mzc3NzUxNTQsLTE2MjMxNjU2
MzhdfQ==
-->