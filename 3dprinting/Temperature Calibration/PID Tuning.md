# PID Tuning
## Tune your hotend  
1. Unload filament (So you don't cook it)
2. Run the following gcode
```
M303 E0 S215 C8
```
Note: Where 215 is the temp in C that you are going to use for your filament (Change accordingly).   
Note: This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D
  
3. Add the results to your slicer config
Edit the start gcode for the printer profile
    ```
    {if first_layer_temperature[0]>210 && first_layer_temperature[0]<220}
    M301  [C<value>] [D<value>] [E<index>] [I<value>] [L<value>] [P<value>]
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
eyJoaXN0b3J5IjpbMTQ0ODg2MDQwNCwtMTc1ODMyNDM3MSw3OT
Y2NDM1MTIsLTY2MDEyNTU3NywxNjMwNDgzMTkxLDYzNjcxNDAx
OSwtMTMwODI5NzAxNF19
-->