# Config
```
#define AUTO_BED_LEVELING_UBL

#define RESTORE_LEVELING_AFTER_G28

#define MESH_INSET (abs(X_PROBE_OFFSET_FROM_EXTRUDER) - 10)

#define MESH_EDIT_GFX_OVERLAY   // Display a graphics overlay while editing the mesh
#define G26_MESH_VALIDATION
#define EEPROM_SETTINGS // Enable for M500 and M501 commands
```

# Operation
1. Reset to defaults

        M502

2. Save to eeprom

        M500

 3. Current eeprom settings
 
        M501
         
 4. Preheat bed and hotend
     Note: Wait for the bed to come up to temp before starting on the hot end. No reason to cook plastic. Also if possible remove the filament before doing this.
     
	 *PLA*
	```	 
	M140 S65 ; heat up the bed
	M104 S215 ; heat up the hot end
	```
	*ABS*
	```	 
	M140 S100 ; heat up the bed
	M104 S255 ; heat up the hot end
	```
	
3. Probe bed
    ```
    G28 ; Home Z
    G29 P1 V3 ; Probe the bed 
    ```
    Note: 
4. Check out the output
    ```
    G29 T
    ```
    Note: Any points listed with a `.` are probably outside the probe limits and ___must___ be interpolated
5. Interpolate missing border points

	```
	G29 P3
	G29 T
	```
	Note: repeat all points are interpolated
	
6. Save Mesh
    ```
    G29 S1 // S1 for PLA S2 for ABS
    ```
7. Set Fade height
    ```
    G29 F10.0
    ```
     Gradually fade out the compensation by 10mm  
8. Activate the UBL
    ```
    G29 A
    ```
9. Save the settings
    ```
    M500
    ```

# Set probe offset
1. Clear current
M851 Z0
2. Home and center
G28 
3. Disable software endstops
M211 S0
4. Adjust down till you touch paper
5. See setting
M114
That's your offset Z-0.71 Z-2.56 Z-1.0
6. Set in firmware
#define Z_PROBE_OFFSET_FROM_EXTRUDER -0.71
7. Do in terminal
M851 Z-0.71
M500 //to save
8. Run mesh validation print
    ```
    G28
    G26 P10 //P10 primes with 10 mm of filament
    ```
10. Resave
 G29 S1
 M500
 # Fine Tuning Mesh
 Use LCD go into mesh edit
 scroll to point and adjust using paper
 Will 
 will automat Tuning the bed
  
 12. [https://www.youtube.com/watch?v=ONpKxkil16Q](https://www.youtube.com/watch?v=ONpKxkil16Q) 13.58
 13.  
 1
# Loading a mesh
G29 L2 // to load 2nd slot

# Pre Print Mesh Tilt
G29 L1 // Load mesh one
G29 J

### Troubleshooting
[https://github.com/MarlinFirmware/Marlin/issues/7508](https://github.com/MarlinFirmware/Marlin/issues/7508)
[http://marlinfw.org/docs/gcode/G029-ubl.html](http://marlinfw.org/docs/gcode/G029-ubl.html)

```
Bed Topography Report:
    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.116  +0.212  +0.309  +0.366  +0.440  +0.477  +0.517  +0.580    .
   |
 7 |   .     +0.010  +0.097  +0.178  +0.259  +0.334  +0.375  +0.431  +0.487    .
   |
 6 |   .     -0.101  -0.046  +0.060  +0.125  +0.207  +0.292  +0.352  +0.405    .
   |
 5 |   .     -0.216  -0.150  -0.068  +0.004  +0.097  +0.169  +0.245  +0.300    .
   |
 4 |   .     -0.315  -0.261 [-0.155] -0.100  -0.011  +0.075  +0.142  +0.215    .
   |
 3 |   .     -0.405  -0.338  -0.253  -0.181  -0.093  -0.011  +0.057  +0.110    .
   |
 2 |   .     -0.456  -0.388  -0.293  -0.221  -0.138  -0.070  -0.003  +0.030    .
   |
 1 |   .     -0.564  -0.469  -0.366  -0.293  -0.221  -0.168  -0.141  -0.097    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)
Bed Topography Report:
    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.028  +0.119  +0.229  +0.290  +0.349  +0.389  +0.447  +0.512    .
   |
 7 |   .     -0.057  +0.035  +0.125  +0.190  +0.254  +0.304  +0.360  +0.415    .
   |
 6 |   .     -0.158  -0.053  +0.037  +0.094  +0.149  +0.218  +0.260  +0.329    .
   |
 5 |   .     -0.251  -0.163  -0.070  -0.011  +0.062  +0.110  +0.172  +0.227    .
   |
 4 |   .     -0.343  -0.260 [-0.151] -0.091  -0.037  +0.019  +0.065  +0.132    .
   |
 3 |   .     -0.463  -0.363  -0.260  -0.190  -0.141  -0.086  -0.021  +0.035    .
   |
 2 |   .     -0.519  -0.453  -0.335  -0.278  -0.213  -0.156  -0.078  -0.041    .
   |
 1 |   .     -0.636  -0.536  -0.438  -0.363  -0.305  -0.259  -0.208  -0.171    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)

    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.290  +0.342  +0.384  +0.397  +0.415  +0.420  +0.443  +0.464    .
   |
 7 |   .     +0.177  +0.225  +0.256  +0.287  +0.304  +0.317  +0.347  +0.353    .
   |
 6 |   .     +0.074  +0.093  +0.145  +0.157  +0.192  +0.212  +0.239  +0.273    .
   |
 5 |   .     -0.048  -0.036  -0.002  +0.035  +0.076  +0.102  +0.132  +0.157    .
   |
 4 |   .     -0.153  -0.150 [-0.088] -0.075  -0.038  +0.011  +0.037  +0.060    .
   |
 3 |   .     -0.233  -0.230  -0.182  -0.145  -0.108  -0.076  -0.060  -0.038    .
   |
 2 |   .     -0.275  -0.270  -0.214  -0.190  -0.155  -0.146  -0.125  -0.103    .
   |
 1 |   .     -0.388  -0.338  -0.308  -0.267  -0.243  -0.235  -0.237  -0.233    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)

Bed Topography Report:
    ( 13,187)                                                              (187,187)
        0       1       2       3       4       5       6       7       8       9
 9 |   .       .       .       .       .       .       .       .       .       .
   |
 8 |   .     +0.254  +0.292  +0.329  +0.344  +0.372  +0.379  +0.379  +0.400    .
   |
 7 |   .     +0.134  +0.175  +0.194  +0.235  +0.250  +0.265  +0.287  +0.295    .
   |
 6 |   .     +0.029  +0.072  +0.107  +0.137  +0.144  +0.177  +0.195  +0.205    .
   |
 5 |   .     -0.067  -0.032  -0.010  +0.019  +0.042  +0.060  +0.087  +0.107    .
   |
 4 |   .     -0.168  -0.141 [-0.093] -0.071  -0.063  -0.023  -0.012  +0.012    .
   |
 3 |   .     -0.263  -0.228  -0.186  -0.161  -0.145  -0.123  -0.100  -0.080    .
   |
 2 |   .     -0.308  -0.295  -0.255  -0.228  -0.203  -0.180  -0.163  -0.156    .
   |
 1 |   .     -0.428  -0.378  -0.350  -0.312  -0.275  -0.277  -0.273  -0.273    .
   |
 0 |   .       .       .       .       .       .       .       .       .       .
        0       1       2       3       4       5       6       7       8       9
    ( 13, 13)                                                              (187, 13)
```  

```
Recv: Bed Topography Report: Recv: Recv:     (  1,199)                                                              (199,199) 
Recv:         0       1       2       3       4       5       6       7       8       9 
Recv:  9 |   .       .       .       .       .       .       .       .       .       . 
Recv:    | 
Recv:  8 |   .     +0.194  +0.190  +0.223  +0.250  +0.253  +0.267  +0.322  +0.402    . 
Recv:    | 
Recv:  7 |   .     +0.115  +0.092  +0.110  +0.127  +0.140  +0.175  +0.232  +0.335    . 
Recv:    | 
Recv:  6 |   .     +0.070  +0.022  +0.042  +0.070  +0.080  +0.101  +0.170  +0.270    . 
Recv:    | 
Recv:  5 |   .     +0.031  -0.018  -0.013  +0.003  +0.022 [+0.053] +0.110  +0.212    . 
Recv:    | 

Recv:  4 |   .     +0.005  -0.048  -0.040  -0.035  -0.023  +0.015  +0.077  +0.162    . 
Recv:    | 
Recv:  3 |   .     -0.002  -0.053  -0.065  -0.065  -0.055  -0.020  +0.017  +0.115    . 
Recv:    | 
Recv:  2 |   .     +0.015  -0.030  -0.043  -0.033  -0.040  -0.014  +0.010  +0.069    . 
Recv:    | 
Recv:  1 |   .     -0.001  -0.040  -0.035  -0.035  -0.047  -0.050  -0.038  +0.007    . 
Recv:    | 
Recv:  0 |   .       .       .       .       .       .       .       .       .       . 
Recv:         0       1       2       3       4       5       6       7       8       9 
Recv:     (  1,  1)                                                              (199,  1)

Recv: Bed Topography Report: Recv: Recv:     (  1,199)                                                              (199,199) 
Recv:         0       1       2       3       4       5       6       7       8       9 
Recv:  9 | +0.273  +0.273  +0.287  +0.335  +0.373  +0.365  +0.360  +0.413  +0.470  +0.527 
Recv:    | 
Recv:  8 | +0.198  +0.194  +0.190  +0.223  +0.250  +0.253  +0.267  +0.322  +0.402  +0.482 
Recv:    | 
Recv:  7 | +0.138  +0.115  +0.092  +0.110  +0.127  +0.140  +0.175  +0.232  +0.335  +0.437 
Recv:    | 
Recv:  6 | +0.118  +0.070  +0.022  +0.042  +0.070  +0.080  +0.101  +0.170  +0.270  +0.370 
Recv:    | 
Recv:  5 | +0.079  +0.031  -0.018  -0.013  +0.003  +0.022 [+0.053] +0.110  +0.212  +0.313 
Recv:    | 
Recv:  4 | +0.058  +0.005  -0.048  -0.040  -0.035  -0.023  +0.015  +0.077  +0.162  +0.246 
Recv:    | 
Recv:  3 | +0.048  -0.002  -0.053  -0.065  -0.065  -0.055  -0.020  +0.017  +0.115  +0.213 
Recv:    | 
Recv:  2 | +0.060  +0.015  -0.030  -0.043  -0.033  -0.040  -0.014  +0.010  +0.069  +0.128 
Recv:    | 
Recv:  1 | +0.038  -0.001  -0.040  -0.035  -0.035  -0.047  -0.050  -0.038  +0.007  +0.052 
Recv:    | 
Recv:  0 | +0.038  -0.001  -0.040  -0.027  -0.035  -0.047  -0.050  -0.038  +0.007  +0.052 
Recv:         0       1       2       3       4       5       6       7       8       9 
Recv:     (  1,  1)                                                              (199,  1) 
Recv: 
Recv: ok [...] 

Send

Autoscroll  showing 256 lines (227 of 483 tota
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc3NzA3OTc3NywxMTc3NjkxNzkzLDI0Mj
EzMzg5LDE1NTAwMzE2MjksLTE0MzA0ODE5MzksMTAwNTIzNjk3
Myw1MzQzNDY1NTIsMTU0NjU5Njg3MywtNDYzNzM0OTY1LDIwMj
gxNzE2NTksLTE3MTA3Mzg1NzksLTY3NjgxOTg3NiwxMTU4Mzcx
ODYwLC0xMDczNDk1NjcyLDI3NDIwNTYxNywxMTQ3Njg5MTEwLD
Q4MjUyNDMzMl19
-->