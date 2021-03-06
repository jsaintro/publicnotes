# PID Tuning
## Pre-flight
1. Unload filament (So you don't cook it)
    `Change Filament/Unload Filament` (Marlin LCD)
    
## Tune your heatbed  

1. You will be testing a full range bed temps
   XXX = 55,65,75,85,95,105,115
2. Run the following gcode
```
M303 E-1 S65 C8
Recv:  Classic PID
Recv:  Kp: 122.48
Recv:  Ki: 7.31
Recv:  Kd: 513.35
```
 This will heat the heat bed (E-1), and cycle around the target temperature 8 times (C8) at the given temperature (S65) ,65 C, and return values for P I and D
  
 3. Add the results to your slicer config
Edit the start gcode for the printer profile

    ```
    {if bed_temperature[0]>=110 && bed_temperature[0]<120}
    M304 PXXX IXXX DXXX
    {elsif bed_temperature[0]>100}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>90}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>80}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>70}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>60}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>50}
    M304 PXXX IXXX DXXX
    {endif}
    ``` 
      Note: Replace the XXXs with our actual PID values that are output from the previous step

## Tune your hotend
Note: Hotend should should be at room temp before starting this  
1. You will be testing a full range of temps
   XXX = 180,1,0,20,20,20,240,250,260,270
   
4. Run the following gcode
```
M303 E0 SXXX C8
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
Note: Where XXX is the temp in C that you are going to use for your filament (Change accordingly).   
Note: This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D.  Ex P=20.95 I=1.51 D=72.77
  
5. Add the results to your slicer config
Edit the start gcode for the printer profile
    ```
    {if first_layer_temperature[0]>=260 && first_layer_temperature[0]<270}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>250}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>240}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>230}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>220}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>210}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>200}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>190}
    M301 E0 PXXX IXXX DXXX
    {endif}
    ```
    Note: Replace the XXXs with our actual PID values that are output from the previous step

## Tune your heatbed  

2. You will be testing a full range bed temps
   XXX = 55,65,75,85,95,105,115
1. Run the following gcode
```
M303 E-1 S65 C8
Recv:  Classic PID
Recv:  Kp: 122.48
Recv:  Ki: 7.31
Recv:  Kd: 513.35
```
 This will heat the heat bed (E-1), and cycle around the target temperature 8 times (C8) at the given temperature (S65) ,65 C, and return values for P I and D
  
 3. Add the results to your slicer config
Edit the start gcode for the printer profile
    ```
    ```
    {if bed_temperature[0]>=110 && bed_temperature[0]<120}
    M304 PXXX IXXX DXXX
    {elsif bed_temperature[0]>100}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>90}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>80}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>70}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>60}
    M304 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>50}
    M304 PXXX IXXX DXXX
    {endif}
    ``` 
      Note: Replace the XXXs with our actual PID values that are output from the previous step
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0NjA1OTAsLTkxODk5NTc2LC0yMDg0Mj
Y3OTU2LC05NTEwNzY1MiwtNDA1NTA0NzE0LC0yOTE5OTE0MTks
MTAxMzU4MjM2MywtNDA0MjU1NTU0LDk5NjY2Njk1OCwtMTc1OD
MyNDM3MSw3OTY2NDM1MTIsLTY2MDEyNTU3NywxNjMwNDgzMTkx
LDYzNjcxNDAxOSwtMTMwODI5NzAxNF19
-->