## Ubuntu
### Add serial permission for user

    sudo gpasswd --add ${USER} dialout

### Install

1. Download software
    [Arduino SW Link](https://www.arduino.cc/en/Main/Software)
    Note: Don't use repo one.  It's old and buggy

2. Uncompress

       tar xf arduino-1.8.7-linux64.tar.xz

3. Move to opt

       sudo mv  arduino-1.8.7-linux64 /opt

4. Fix the desktop icon name

       suod

## Configure to talk to 3d printer

1.  Plug in the arduino via the USB cable (Should power up (Including LCD)
2. Select the model
3. Tools/Board/Arduino/Genuino Mea or Mega 2560
4. CPU should be Mego 2560
5. Select the port (Should only have one in the dropdown)
6. Select Board Info (Should verify above settings)

## Windows
### Install Arduino SW
1. Download
[Arduino SW Link](https://www.arduino.cc/en/Main/Software)
1. Install
1. Plug in the Arduino via USB cable
* Make sure to install usb driver For windows 10 this should be automatic

        
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg0OTE5ODc4NCwtMTU1MTcxNTY5NywtMj
ExOTkyMjY1MiwxMzEwODk0ODE4LDgxMjE3NTM4M119
-->