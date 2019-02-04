# Z Stepper Calibration
This procedure is to get both Z steppers in sync so the build plane is as level as possible


1. Rough Calibration
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
            Bilinear Leveling Grid:
                  0      1
            0 +0.492 +1.020
            1 +0.731 +0.574
        Note: In this case right stepper needs to be adjusted lower
    3. Adjust rights stepper
        - CW is lower
        - CCW is higher
     4. Repeat Calibration loop until left and right sides match

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg1NTA5NTQzNywxNzg3ODgyODJdfQ==
-->