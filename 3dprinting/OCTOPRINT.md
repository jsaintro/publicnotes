# Hardware
* Raspberry Pi 3
* External USB power should be 2.5A
* typical is 400ma so probably good at 1A
* SD Card (Class 10) at lest 4GB More like 16GB


# Install Octopi
1. Download/Install the imaging software (Etcher)
	1. Download the latest version here
        https://www.balena.io/etcher/
	2. Create a app folder and move the zip file there
	   
	       mkdir ~/etcher
	       mv balena-etcher-electron-1.5.71-linux-x64.zip ~/etcher/
	       cd ~/etcher
	       unzip balena-etcher-electron-1.5.71-linux-x64.zip
	       chmod +x 
	       
	3. Create a etcher.desktop shortcut
	   Note: Do this nexttime or figure out how to have appimage automatically do this in gnome
	4. Launch etcher
	5.        
2. Download the latest image
    https://octopi.octoprint.org
    Note: no need to decompress (etcher will do this automatically)

3. Flash img file to SD
# Configure Octopi Network
1. Mount SD card on workstation and access the `boot` partition
2. On card edit octopi-wpa-supplicant.txt

        vi octopi-wpa-supplicant.txt
        ## WPA/WPA2 secured
        network={
    On card edit octopi-network.txt
   ```
   ## WPA/WPA2 secured
   iface wlan-octopi inet manual
      wpa-ssid= "put SSID here"
          wpa-psk= "put password here"
        }
        country=US # United States

3. Eject both partitions `boot` and `root`       ```
# Boot raspberrypi
1. install sd card
2. Power on printer (So we don't power printer from raspberry pi)
   Note: have to figure out how to configure this
3. connect usb to printer
4. Connect usb power to raspberry pi
5. Should see lights bliking
6. Check access point for ip address assigned to octopi
   Note: for your AP it will get a DNS of octopi.saint-rossy.net automatically
7. ssh into octopi (do this before accessing web interface)

	ssh pi@octopi
   Note: if ssh is inaccessible do a hard reboot
   default credentials are: pi/raspberry
8. Change the default password
   passwd
9. Initial Config
   ```
   sudo raspi-config
   ```
   expand the filesystem
   Advanced Optons/
   select "Finish"
10. Access via a web browser
   http://octopi
11. Set a username and password
12. Login (ignore any updates for now)
# Configure the raspberrypi
1. ssh into the raspberry pi

and do any recommended updates

# Install Firmware Updater
Install the plugin by the octopi creator
Install avrdude from the command line
  sudo apt install avrdude
Restart octoprint server (maybe twice)
Will appear under settings plugins heading
Configuration
flashmethod avrdude
AVR MCU ATmego2560
Path: /usr/bin/avrdude
AVR Programmer Type: stk500v2
baud rate: 115200

Edit arduino ide preferences and set a not temp location for builds
Exit the arduino IDE (it overwrites the preferences file on exit)
/home/jsaintrocc/.arduino15/preferences.txt
build.path=/home/jsaintrocc/ArduinoBins/

## To install FW
### Marlin
#### Plugin config
Flash method: avrdude (Atmel AVR Family)
AVR MCU: ATmega2560
Path to avrdude: /usr/bin/avrdude
AVR Programmer Type: stk500v2

#### Path
Select from filesystem /home/jsaintrocc/ArduinoBins/Marlin.ino.hex

### Prusa
#### Plugin config
Flash method: avrdude (Atmel AVR Family)
AVR MCU: ATmega2560
Path to avrdude: /usr/bin/avrdude
AVR Programmer Type: wiring

#### Path
    ```
    /Documents/gitstuff/PF-build-hex/FW392-Build3524/BOARD_EINSY_1_0a/FW392-Build3524-1_75mm_MK3S-EINSy10a-E3Dv6full-EN_ONLY.hex
    ```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTgzOTMxMTgsLTgyMTY0NTA2NywtMT
Q4MTg5ODcyNiwyNzc2NDkzMTYsLTc0NjQxNTA0NCwtNDU3NDYw
NjkxLC0yODExOTc4NzgsNDQyOTE0MjA0LDkyNzcxNTY4LDk1ND
gwMzAzMCw4NTYzMTczNzcsMTc0NDM2MTA5MiwxOTQzODU3MzQx
LDEyNTU2NzM4MzRdfQ==
-->