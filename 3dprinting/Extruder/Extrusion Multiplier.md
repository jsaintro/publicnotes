# Extrusion Multiplier
1. Download this [cube STL](https://www.thingiverse.com/thing:3071464)
2. Use theses settings in Prusa Slicer
|Key|Value|
|--|--|
|Slicing Profile
|Perimiters|1|
|top layers|0|
|bottom layers|0|
|infill|0|
|default extrusion width|0.45|

* 1 perimiter
* 0 top/bottom layer
* 0 infill
* default extrusion width 0.45 (print settings/advanced) this should be the default
* Use .2mm Quality MK3 profile
* spiral vase mode
* Disable K value (Comment out line in filament gcode)
* Disable any current extrusion multiplier 
/Documents/3dprinter/calibration/cube/extrusion_cubeABS.3mf

Print cube

measure 
Note there always seems to be one wall that's a little thinner.  as long as you have one x and one y consistent go for it.
Take an average of multiple points and sides
48
56
48
52
50
54
49
50
57
56
=52ave
desired wall thickness/measured wall thickness * extrusion multiplier = new extrusion multiplier

.45/.48 * 1 = .9375

adjust extrusion multiplier

etc...

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDcyNTkzODUsLTE3MDAyNjM3NzMsLT
E1MDAxODMwNzYsLTE1MTkwMTAwNDYsLTg4MjIyMjEwMiwtMTE5
MDY4MjQ3NywxNTMyNjIwOTc1LC0xNDgwOTY0ODIsLTI2OTEwNj
U2OCwtMTYyNTMyOTkzMSwxOTQ1OTkwNTU0XX0=
-->