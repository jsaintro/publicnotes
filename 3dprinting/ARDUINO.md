## Add serial permission for user

```
sudo gpasswd --add ${USER} dialout
```

1. Install

        don't install the one in the repos
        Download from the site
        https://www.arduino.cc/en/Main/Software
        

## Configure to talk to 3d printer

1.  Plug in the arduino via the USB cable (Should power up (Including LCD)
2. Select the model
3. Tools/Board/Arduino/Genuino Mea or Mega 2560
4. CPU should be Mego 2560
4. Select the port (Should only have one in the dropdown)
5. Select Board Info (Should verify above settings)

        
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMTk5MjI2NTIsMTMxMDg5NDgxOCw4MT
IxNzUzODNdfQ==
-->