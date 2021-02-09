
## Soup to Nuts of Tuning your 3D Printer

Note: Try https://teachingtechyt.github.io/calibration.html calibration guide. Looks good!

1. ARDUINO
2. MARLIN-1.1.9
3. Maintenance/Monthly
4. Maintenance/Preflight
5. PID Tuning
6. Z Stepper Calibration
7. PRONTERFACE

### Initial printer calibration
1. Go through the wizard to start with (Prusa FW only)
2. Do [temperature calibration](https://help.prusa3d.com/en/article/temperature-calibration_133266) 
	1. With enclosure door open
	2. This takes forever!! Probably about 1 hour. 70c takes particularly long time. Eventually with BLtouch or SuperPinda you won't need to do this.
3. Steps calculators https://blog.prusaprinters.org/calculator_3416/ (Also other useful calculators)
4. [See Teaching Tech's Frame Check](https://teachingtechyt.github.io/calibration.html#frame)
5. Temperature Calibration/PID Tuning
6. `Bed Calibration/UBL Unified Bed Leveling` (Marlin Only)
7. `Bed Calibration/(Prusa/Marlin) 1st Layer` also look at [Teching Tech's First Layer Guide](https://teachingtechyt.github.io/calibration.html#firstlayer)
8. Baseline print https://teachingtechyt.github.io/calibration.html#baseline
9. Extruder/Esteps Stepper Calibration alt: https://teachingtechyt.github.io/calibration.html#esteps (Skip this if using bondtech)
10. Extruder/Extrusion Multiplier https://teachingtechyt.github.io/calibration.html#flow (This is different from MK3s and Gen1.5) This guide may be better https://guides.bear-lab.com/Guide/Extrusion+multiplier+and+filament+diameter/8?lang=en
11. Retraction tuning https://teachingtechyt.github.io/calibration.html#retraction
12. Stepper Calibration/Linear Advance Calibration
### Per plastic type
1. Look through the guides

### Per Filament Calibrations
1. 1st layer Calibration
2. Extruder/Extrusion Multiplier
4. Stepper Calibration/Linear Advance Calibration
5. Retraction tuning https://teachingtechyt.github.io/calibration.html#retraction
6. Follow this guide https://teachingtechyt.github.io/calibration.html#temp
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExOTIyNDA4LC0yNjAyMTE3MCwxMDM1Mz
Y2Mjc0LC04MTc4Mzk5MzQsMTc0MDg1NzI0LC0yMjk1Mzc5Nzks
MTYyOTkxNzYyMSwxNDI5NDAxNDEsMTk2MTYwMDI3MywtNDI4Nz
E4NjkwLC0xMDgxMTk2Nzg1LDExMTc3ODY2MDYsNTI2MTAwMzYy
LDE2NDYyMDg0OSwtMTE0MDE1MzUsLTc2OTQ3Mjc1NywtNzI5Mz
c0MDY0LDUxMDQ3MDA2MSw4MTk2NjIyMDQsNTk2OTY1MDg2XX0=

-->