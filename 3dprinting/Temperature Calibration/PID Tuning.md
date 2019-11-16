# PID Tuning
## Tune your hotend  
1. Unload filament (So you don't cook it)
2. Run the following gcode
```
M303 E0 S215 C8
Send: M303 E0 S215 C8
Recv: PID Autotune start [...]
Recv:  bias: 93 d: 93 min: 211.67 max: 220.81 [...]
Recv:  bias: 90 d: 90 min: 211.56 max: 218.33 [...]
Recv:  bias: 90 d: 90 min: 211.67 max: 218.23
Recv:  Ku: 34.92 Tu: 27.78
Recv:  Classic PID
Recv:  Kp: 20.95
Recv:  Ki: 1.51
Recv:  Kd: 72.77
```
Note: Where 215 is the temp in C that you are going to use for your filament (Change accordingly).   
Note: This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D.  Ex P=20.95 I=1.51 D=72.77
  
3. Add the results to your slicer config
Edit the start gcode for the printer profile
    ```
    {if first_layer_temperature[0]>210 && first_layer_temperature[0]<220}
    M301 E0 P20.95 I1.51 D72.77
    {endif}
    ```
Note: Consider wrapping this in an if statement



 
## Tune your heatbed  

1. Run the following gcode
`M303 E-1 S65 C8`
 This will heat the heat bed nozzle (E-1), and cycle around the target temperature 8 times (C8) at the given temperature (S65) ,65 C, and return values for P I and D
  
 3. Add the results to your slicer config
Edit the start gcode for the printer profile
`M304 [D<value>] [I<value>] [P<value>]`
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDA4ODg1MDYxLC0xNzU4MzI0MzcxLDc5Nj
Y0MzUxMiwtNjYwMTI1NTc3LDE2MzA0ODMxOTEsNjM2NzE0MDE5
LC0xMzA4Mjk3MDE0XX0=
-->