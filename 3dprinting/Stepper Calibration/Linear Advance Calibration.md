
Use this tool to generate the gcode
[http://marlinfw.org/tools/lin_advance/k-factor.html](http://marlinfw.org/tools/lin_advance/k-factor.html)
For our prusa Mk3

 - Nozzle Temp: 215
 - Bed Temp: 65
 - Slow speed printing 20mm
 - Fast speed printing 60mm
	 - Note this should be the slowest/fastest speeds during a single print (So for Speed do 20-60 etc..) bigger spreads have 
 - Movement Speed 180mm
 - retract speed 35
 - retract distance .8
 - Accelleration: 800
 - ending k value: 50
 - k value steps 5
 - extrusion multiplier

Note: For prusa you don't have to add any ABL it'll do it automatically when it homes apparently

1. Evaluate
  With a magnifying glass loop at the 1st transition line (at the top)
  You're looking for the line that seems most consistent through the transition Doesn't got thin->thick or vice versa
30

2. File tune repeat above but set the scale  +-5 and steps to 0.5
26
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE0MjIxMDgsMjA2OTU4MTU4NSwxMTA3Nz
k0MjE3LDE5NjcwODcyMjYsMTMwOTI2MDY0LDIxNDczMDI0NTEs
OTgwNjg2MDkwLC0yMDM1MTk2ODZdfQ==
-->