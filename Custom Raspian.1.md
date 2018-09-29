# Custom Raspian

1. Git clone the build project
   `git clone https://github.com/RPi-Distro/pi-gen.git`
2. Generate the config file
   `echo IMG_NAME='Raspbian' >> config`
3. Skip stages we don't want to compile
   ```
   touch ./stage3/SKIP ./stage4/SKIP ./stage5/SKIP
   rm stage4/EXPORT* stage5/EXPORT*
   ```
4. Use docker to compile the image
   `./build-docker.sh`
5. Completed builds will be in the `deploy/` folder

# Writing the image to an SD
1. Download etcher 
   https://etcher.io/
1. Select your image and flash to the SD
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjkyNjU3MDgxXX0=
-->