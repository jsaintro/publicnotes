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
   

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1Njk0MjU1Niw5MzkzMDkwNTIsMTQyOT
UxODAzOSwtMTc5ODI1ODQ4NCwxMzEzNzcwODQ2LDQxNzk4MTM1
OSw3MjE2MDAyNCwyMDY2NTg2MzExLC0xNDU3ODk4NDExLC02NT
EyMDM4NTksMTYyMDYxMTgzMiwtNDEyNzI2MTg2LC01ODYyMDcz
MzQsODAxNDczNzY1LC0zOTY1OTM1OTgsNjk4MTEzMjYxXX0=
-->