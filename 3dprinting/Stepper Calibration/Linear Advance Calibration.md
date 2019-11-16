
Use this tool to generate the gcode
[http://marlinfw.org/tools/lin_advance/k-factor.html](http://marlinfw.org/tools/lin_advance/k-factor.html)
For our prusa Mk3

 - Nozzle Temp: 215
 - Bed Temp: 65
 - Slow speed printing 45mm
 - Fast speed printing 60mm
 - Movement Speed 180mm
 - retra
 - Accelleration: 800

Add 
```
G28 W ; home all without mesh bed level
G80 ; mesh bed leveling
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg0MjI0MDQ4LDk4MDY4NjA5MCwtMjAzNT
E5Njg2XX0=
-->