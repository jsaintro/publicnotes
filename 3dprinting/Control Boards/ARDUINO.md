## Ubuntu Setup
### Add serial permission for user

    sudo gpasswd --add ${USER} dialout

### Install

1. Download software
    [Arduino SW Link](https://www.arduino.cc/en/Main/Software)
    Note: Don't use repo one.  It's old and buggy

2. Uncompress

       tar xf arduino-1.8.7-linux64.tar.xz

3. Move to opt

       sudo mv arduino-1.8.7-linux64/arduino-1.8.7 /opt

4. Install

       cd /opt/arduino-1.8.7
       ./install.sh

## Windows Setup
### Install 
1. Download
[Arduino SW Link](https://www.arduino.cc/en/Main/Software)
1. Install
1. Plug in the Arduino via USB cable
* Make sure to install usb driver For windows 10 this should be automatic

## Configure IDE to talk to 3D printer

1.  Plug in the arduino via the USB cable (Should power up (Including LCD)
2. Select the model
3. Tools/Board/Arduino/Genuino Mea or Mega 2560
4. CPU should be Mega 2560
5. Select the port (Should only have one in the dropdown)
6. Select Board Info (Should verify above settings)



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYxMDI1MjY4XX0=
-->