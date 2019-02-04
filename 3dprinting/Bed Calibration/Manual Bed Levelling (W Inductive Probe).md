
# Manual Bed Levelling

Using the inductive probe get the bed as level as possible (This way the SW bed levelling won't have to work as hard)

1. Sync the Z axis steppers
	1. Run z-axis up to top of frame until both Z-steppers start skipping on top
2. Home All Axis

        G28
4. Set firmware to only do 4 points
  
        #define GRID_MAX_POINTS_X 2      
3. Begin Calibration loop
   1. Perform Mesh Bed Leveling

            G29
   2. Review report and look for difference between left side and right side

            Bilinear Leveling Grid:
                  0      1
            0 +0.492(FL) +1.020(FR)
            1 +0.731(BL) +0.574(BR)
        Note: In this case right stepper needs to be adjusted lower
        
   3. Lock FL tight (This will be your reference)
   4. Adjust FR till it matches FL
   5. Adjust BL and BR together until all points match
   6. Repeat Calibration loop until left and right sides match
1/4 turn is .1mm Shoot for +/- .05
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDc4MTc0MCw0NzU0NTc4MTYsLTcyNj
IwODc4OF19
-->