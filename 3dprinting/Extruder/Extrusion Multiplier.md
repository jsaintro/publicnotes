# Extrusion Multiplier
1. Download this [cube STL](https://www.thingiverse.com/thing:3071464)
2. Use theses settings in Prusa Slicer

|Key|Value|
|--|--|
|Slicing Profile|0.2mm Quality|
|Perimiters|1|
|top layers|0|
|bottom layers|0|
|infill|0|
|default extrusion width|0.45|
|Spiral Vase Mode|True|
|Filament Gcode|Comment out K values|
|extrusion multiplier|1|

3. Print cube
4. Measure
    * Inspect model for layer accuracy 
	    * Is each layer consistently on top of the other for X and Y axis
	    * If not check belts and bearings
    * Take measurements from each side then average all 4 sides together
	    * only measure from top 3rd of print (To avoid elephant foot)
	    * Take average of all measurements

5. Calculate Multiplier

       desired wall thickness/measured wall thickness * extrusion multiplier = new extrusion multiplier
        Ex. 0.45/0.48 * 1 = .9375

6. adjust extrusion multiplier in slicer
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3NTEyMDQxOCwtNTY5MTYxNzYsLTE3MD
AyNjM3NzMsLTE1MDAxODMwNzYsLTE1MTkwMTAwNDYsLTg4MjIy
MjEwMiwtMTE5MDY4MjQ3NywxNTMyNjIwOTc1LC0xNDgwOTY0OD
IsLTI2OTEwNjU2OCwtMTYyNTMyOTkzMSwxOTQ1OTkwNTU0XX0=

-->