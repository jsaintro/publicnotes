# Z Stepper Calibration
This procedure is to get both Z steppers in sync so the build plane is as level as possible

1. Rough Calibration
	1. Run z-axis up to top of frame until both Z-steppers start skipping on top
2. Home All Axis

        G28
3. Begin Calibration loop
    1. Perform Mesh Bed Leveling

            G29
    2. Review report and look for difference between left side and right side

            Bilinear Leveling Grid:
                0     1     2     3
            0 -0.30 -0.17 +0.15 +0.47
            1 -0.29 -0.14 +0.18 +0.48
            2 -0.23 -0.07 +0.24 +0.54
            3 -0.08 +0.10 +0.38 +0.64
               
        Note: In this case right stepper needs to be adjusted lower
    3. Adjust rights st



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNjI2NzUyNDVdfQ==
-->