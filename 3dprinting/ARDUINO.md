## Ubuntu
### Add serial permission for user

```
sudo gpasswd --add ${USER} dialout
```

### Install

1. Download software        don't install the one in the repos
[Arduino SW Link](https://www.arduino.cc/en/Main/Software)
    Note:         Download from the site
        https://www.arduino.cc/en/Main/Software
        

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
eyJoaXN0b3J5IjpbLTEyOTA4ODMxNTUsLTIxMTk5MjI2NTIsMT
MxMDg5NDgxOCw4MTIxNzUzODNdfQ==
-->