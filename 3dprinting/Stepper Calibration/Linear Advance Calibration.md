
Use this tool to generate the gcode
[http://marlinfw.org/tools/lin_advance/k-factor.html](http://marlinfw.org/tools/lin_advance/k-factor.html)
For our prusa Mk3

 - Nozzle Temp: 215
 - Bed Temp: 65
 - Slow speed printing 45mm
 - Fast speed printing 60mm
 - Movement Speed 180mm
 - retract speed 35
 - retract distance .8
 - Accelleration: 800
 - ending k value: 50
 - k value steps 5
 - extrusion multiplier

Add 
```
G28 W ; home all without mesh bed level
G80 ; mesh bed leveling
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMwOTI2MDY0LDIxNDczMDI0NTEsOTgwNj
g2MDkwLC0yMDM1MTk2ODZdfQ==
-->