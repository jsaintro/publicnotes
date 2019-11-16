
Use this tool to generate the gcode
[http://marlinfw.org/tools/lin_advance/k-factor.html](http://marlinfw.org/tools/lin_advance/k-factor.html)
For our prusa Mk3

 - Nozzle Temp: 215
 - Bed Temp: 65
 - Slow speed printing 45mm
 - Fast speed printing 60mm
 - M

Add 
```
G28 W ; home all without mesh bed level
G80 ; mesh bed leveling
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MzI0ODI5NDAsOTgwNjg2MDkwLC0yMD
M1MTk2ODZdfQ==
-->