# PID Tuning
## Tune your hotend  
1. Unload filament (So you don't cook it)
2. You will be testing a full range of temps
   XXX = 195,205,215,225,235,245,255,265
   
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
    M301 E0 PXXX IXXX DXXX
    {elsif bed_temperature[0]>100}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>90}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>80}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>70}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>60}
    M301 E0 PXXX IXXX DXXX
    {elsif first_layer_temperature[0]>50}
    M301 E0 PXXX IXXX DXXX
    {if bed_temperature[0]>60 && bed_temperature[0]<70}
    M304 P122.48 I7.31 D513.35
    {endif}
    ``` 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5ODMxMTkwOSwxMDEzNTgyMzYzLC00MD
QyNTU1NTQsOTk2NjY2OTU4LC0xNzU4MzI0MzcxLDc5NjY0MzUx
MiwtNjYwMTI1NTc3LDE2MzA0ODMxOTEsNjM2NzE0MDE5LC0xMz
A4Mjk3MDE0XX0=
-->