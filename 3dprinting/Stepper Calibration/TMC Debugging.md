# TMC Debugging
## Prusa Firmware
1. Enable TMC service gcodes
```
#define TMC2130_SERVICE_CODES_M910_M918 // enable the cods
//##define TMC2130_DEBUG // enable M122
```
NOTE: even with TMC2130_DEBUG and the R/W defines it sitll doesn't work

2. Print current holding/running values
   M913
You probably want to mess with running currents and SG settings if you have skipped steps
SG for X looks way too high by default
Lower sg = more sensitive 1 = most Max = ?? Maybe -10 to 10?? 





<!--stackedit_data:
eyJoaXN0b3J5IjpbNzcwNDk5Njg2LDI3OTQzMDczOCwzMjYyND
M4MDQsLTg0MjgyMjQxNywxNTI1MzA4Mzc2XX0=
-->