# Extrusion Multiplier
1. Measure filament thickness using digital calipers
	2. Measure several points around the circumerence (Might not be perfectly round)
	3. Might be easier to do if you cut a 30cm length and measure is several spots (avoiding the ends)
	4. Try and apply similar pressure when measuring
	5. Ideally you want to use a micrometer like a (Mitutoyo 102-301)
2. Download this [calibration model](https://www.thingiverse.com/thing:3405991)
3. Use theses settings in Prusa Slicer

|Key|Value|Note|
|--|--|--|
|Print Settings Profile|0.2mm Quality|
|Spiral vase|Check|Accept adjusted values|
|Perimeters|1|
|top layers|0|
|bottom layers|0|
|infill|0|
|default extrusion width|0.45|
|Filament Gcode|Comment out K values|
|extrusion multiplier|1|

3. Print cube
4. Measure
    * Inspect model for layer accuracy 
	    * Is each layer consistently on top of the other for X and Y axis
	    * If not check belts and bearings
    * Take measurements from each side then average all 4 sides together
	    * only measure from top 1/2 of print (To avoid elephant foot)
	    * Take average of all measurements

5. Calculate Multiplier

       desired wall thickness/measured wall thickness * extrusion multiplier = new extrusion multiplier
        Ex. 0.45/0.48 * 1 = .9375

6. adjust extrusion multiplier in slicer
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTk0MDc4MTQ5LC0xNjk3MjM0MTQsLTc3NT
EyMDQxOCwtNTY5MTYxNzYsLTE3MDAyNjM3NzMsLTE1MDAxODMw
NzYsLTE1MTkwMTAwNDYsLTg4MjIyMjEwMiwtMTE5MDY4MjQ3Ny
wxNTMyNjIwOTc1LC0xNDgwOTY0ODIsLTI2OTEwNjU2OCwtMTYy
NTMyOTkzMSwxOTQ1OTkwNTU0XX0=
-->