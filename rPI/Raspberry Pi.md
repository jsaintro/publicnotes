
# Install Raspbian Lite (NOOBS Method)
## Format your SD
2. Download/install formatting tool from
    https://www.sdcard.org/downloads/formatter_4/index.html
    
3. Insert the SD and format (Must be Fat32 for NOOBS)
## Install NOOBS Software
1. Download from here https://www.raspberrypi.org/downloads/noobs/ (Do NOOBS Lite)
2. Extract all the files in the zip
3. Drag and drop to the formatted SD card
4. Eject SD
## Boot Raspberry Pi
1. Hook up HDMI monitor and USB Keyboard Mouse
2. Insert SD into Raspberry Pi and connect to usb power
2. Should see a red light and a blinking green light
3. Should see install screen
## Configure NOOBS install
1. Select wifi network
2. Select distro: Raspbian Lite
3. Select Install
## First Boot
1. Login with pi/raspberry
2. Fix keyboard language
	1. Run config tool

        ```
        $~ sudo raspi-config
        ```

	2. Select "Localisation Options"
	3. Select "Change Keyboard Layout"
	4. Select "Generic 104-key PC"
	5. Select "Other"
	6. Select "English (US)"
	7. Select "English (US)"
	8. Select "The default for the keyboard layout"
	9. Select "No compose key"
4. Update the default editor
   ```
   sudo update-alternatives --set editor /usr/bin/vim.tiny
   ```
## Secure Login
1. create your user
   ```
   sudo useradd -m jsaintrocc
   sudo passwd jsaintrocc (See lastpass)
   ```
1. Add user to all groups
   ```
   sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,spi,i2c,gpio jsaintrocc
   ```
   Note: Adding to sudo group will allow you to use sudo

1. Login as your user and sudo su
2. delete pi default user
   ```
   sudo userdel pi
   ```
1. Change your shell to bash
   ```
   chsh -s /bin/bash jsaintrocc
   ```
## Update System
```
sudo apt update; sudo apt -y dist-upgrade
```

## Add additional port for SSH
Note: This is a workaround for the axlab because google wifi can't forward external ports to same port on different hosts

```
sudo vi /etc/ssh/sshd_config
Port 22
Port 2201
```

## Enable SSH
```
sudo systemctl start ssh
sudo systemctl enable ssh
```

## Change hostname
```
vi /etc/hostname
vi /etc/hosts
reboot
```

## Install NOIP client
1. Setup a new host on the website
2. Install the client
   ```
   mkdir noip
   cd noip
   wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz
   tar xzvf noip-duc-linux.tar.gz
   cd noip-2.1.9-1/
   sudo make
   sudo make install
   ```

3.  Start the client
   ```
   sudo /usr/local/bin/noip2
   ```
4. Verify it's running and check config
   ```
   sudo noip2 -S
   ```

5. Autostart
   1.  Create the init file
   ```
   sudo vi /etc/init.d/noip2
   #! /bin/sh
   # /etc/init.d/noip 

   ### BEGIN INIT INFO
   # Provides:          noip
   # Required-Start:    $remote_fs $syslog
   # Required-Stop:     $remote_fs $syslog
   # Default-Start:     2 3 4 5
   # Default-Stop:      0 1 6
   # Short-Description: Simple script to start a program at boot
   # Description:       A simple script from www.stuffaboutcode.com which will start / stop a program a boot / shutdown.
   ### END INIT INFO

   # If you want a command to always run, put it here

   # Carry out specific functions when asked to by the system
   case "$1" in
     start)
       echo "Starting noip"
       # run application you want to start
       /usr/local/bin/noip2
       ;;
     stop)
       echo "Stopping noip"
       # kill application you want to stop
       killall noip2
       ;;
     *)
       echo "Usage: /etc/init.d/noip {start|stop}"
       exit 1
       ;;
   esac

   exit 0
   ```   

   1. Change the permissions
      ```sudo chmod 755 /etc/init.d/noip2```
   2.  Start it manually
      ```sudo /etc/init.d/noip2 start```
   3. Have it autostart on boot
      ```sudo update-rc.d noip2 defaults```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNDE3NzQyNjddfQ==
-->