# Extrusion Multiplier
1. Download this [calibration model](https://www.thingiverse.com/thing:3405991)
2. Use theses settings in Prusa Slicer

|Key|Value|
|--|--|
|Print Settings Profile|0.2mm Quality|
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
eyJoaXN0b3J5IjpbMTczNTI4MDUwNCwtNzc1MTIwNDE4LC01Nj
kxNjE3NiwtMTcwMDI2Mzc3MywtMTUwMDE4MzA3NiwtMTUxOTAx
MDA0NiwtODgyMjIyMTAyLC0xMTkwNjgyNDc3LDE1MzI2MjA5Nz
UsLTE0ODA5NjQ4MiwtMjY5MTA2NTY4LC0xNjI1MzI5OTMxLDE5
NDU5OTA1NTRdfQ==
-->