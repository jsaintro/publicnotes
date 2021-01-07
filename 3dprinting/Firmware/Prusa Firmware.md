## Build the Firmware
1. Clone the repo
	```
	git clone https://github.com/prusa3d/Prusa-Firmware.git
	```
2. Select the version
    ```
    cd Prusa-Firmware
    git checkout v3.8.0
    ```
3. Fix Dos CR/LF silliness
      ```
   find . -type f -print0 | xargs -0 dos2unix
   ```
      Note: For Linux do `apt-get install dos2unix` to install the utility

4. Run the build script
   ```
   ./PF-build.sh
   ```
	5. Select the MK3S variant (Firmware/variants/1_75mm_MK3S-EINSy10a-E3Dv6full.h) (6)
	6. Select English Only (2)
	7.  Set DEV_STATUS to gold (1)
5. Bin will be in PF-Build-hex directory named *.hex
6. Flash using prusa slicer (or octopi)

## Updating
```
git pull
```
git chechout 

## Prusa BEAR
Download this one instead
https://github.com/bear-lab-3d/Prusa-Firmware/releases
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2ODY1MDUyMDAsMjA1Njk0MjU1Niw5Mz
kzMDkwNTIsMTQyOTUxODAzOSwtMTc5ODI1ODQ4NCwxMzEzNzcw
ODQ2LDQxNzk4MTM1OSw3MjE2MDAyNCwyMDY2NTg2MzExLC0xND
U3ODk4NDExLC02NTEyMDM4NTksMTYyMDYxMTgzMiwtNDEyNzI2
MTg2LC01ODYyMDczMzQsODAxNDczNzY1LC0zOTY1OTM1OTgsNj
k4MTEzMjYxXX0=
-->