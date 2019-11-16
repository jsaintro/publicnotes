# HW Setup
You're using a NODE MCU for this

# Arduino Setup

1.  Download the ST_anything project
    
    ```
    git clone https://github.com/DanielOgorchock/ST_Anything.git ST_Anything_Garage
    cd ST_Anything_Garage
    git checkout v2.9.7
    ```
2. Copy the garage door sketches to your arduino directory
  Note: for Linux the DIR is ~/Arduino

   ```
   cp -r ST_Anything_Garage/Arduino/Sketches/ST_Anything_GarageDoors_ESP8266WiFi/ ~/Arduino/ST_Anything_GarageDoors_ESP8266WiFi
   cp -r ST_Anything_Garage/Arduino/libraries/* ~/Arduino/libraries/
   ```

3. Download the board libraries
	4. IN arduino go into preferences and add into `Additional boards Manager`
        http://arduino.esp8266.com/stable/package_esp8266com_index.json
	5. Now open up the board and click the board manager at the bottom you should be able to install the esp8266 lib now
	6. Now you'll be able to select Generic ESP8266 Module
4. Edit sketch
    ```
    #define D1  5
    #define D2  4
    #define D5 14
    #define D6 12
    ```
5. Verify IDE by compiling the sketch

6. Prep nodemcu for flashing
Use baud rate 115200 (Note: if it doesn't show up make sure you're using a microUSB DATA cable
defaults are fine
write down the MAC from the serial monitor
8. [https://github.com/nodemcu/nodemcu-devkit-v1.0](https://github.com/nodemcu/nodemcu-devkit-v1.0)
9. MAC: 60:01:94:51:bd:a1

# Setup smartthings device handler
1.  Login to the  [smarthings api](https://graph.api.smartthings.com/login/auth) (USe the samsung login with your ST credentials
-   Click on "My Device Handlers" from the navigation menu.
-  Enable github integration
-   Click on "Settings" from the menu and add my GitHub Repository to your account
    -   Owner: DanielOgorchock
    -   Name: ST_Anything
    -   Branch: master
-   Click on "Update From Repo" from the menu
-   Select "ST_Anything (master)" from the list
-   Select all of the Parent and Child Device Handlers
-   Check the "Publish" check box and click "Execute Update"
-   You should now have all of the necessary Device Handlers added to your account
## SmartThings Device Handler Instructions - FOR USE WITH LAN-to-HUB WiFi/Cat5 Ethernet Devices

-   Click on My Devices from navigation menu
-   Click the "+ New Device" button from the menu
-   Enter in the following REQUIRED fields
    -   Name: anything you want (tip: keep it short)
    -   Label: anything you want (tip: keep it short)
    -   Device Network ID: any unique name (this will be overwritten with your device's MAC address automatically)
    -   Type: "Parent_ST_Anything_Ethernet"
    -   Version: "Self Published"
    -   Location: your location (required!)
    -   Hub: your hub (required!)
-   Click the Create button at the bottom of the screen
-   On your phone's SmartThings app, select Things view, find and select your New Device
    -   You may receive a "Device not fully configured" pop-up with the ST app. We're about to take care of that!
-   In the Arduino Device, click the "Gear Icon" in the top right of the screen
-   Enter the folowing data from your Arduino
    -   IP Address: must match what you hard-coded in your Arduino sketch file
    -   Port: must match what you hard-coded in your Arduino sketch file
    -   MAC Address: must match your Arduino's MAC address, all uppercase, no delimiters (e.g. 06AB12CD34EF)
    -   Configure the correct number of "Button Devices" to match what you defined in the Arduino Sketch. Set to 0 if none. Note: If you visit the "Recently" page of your Parent Device in your ST App on your phone, you may get an annoying warning that the setup is not complete. If you've entered all of the required data above, you can safely ignore this message. Once it scrolls off the 'Recently' list, the pop-ups will stop.
#### Internal pull-up/-down resistors

GPIO 0-15 all have a built-in pull-up resistor, just like in an Arduino. GPIO16 has a built-in pull-down resistor.

~/Arduino/ST_Anything_GarageDoor_ESP8266WIFI
  ST_Anything_Garage/Arduino/Sketches/ST_Anything_GarageDoor_ESP8266WIFI


# Pairing SmartThings shield with hub

1.  Power on the Arduino with shield attached
2.  Put it into pairing mode (If it’s been paired before)  
    Hold the  `switch`  button for 6 seconds (Red light should come on)
3.  In the App go into pairing mode looking for a device
4.  Hit the “switch” button on the shield (Unless you already did the 6 second hold ???)
5.  Should pair as an Arduino ThingShield

# Setup the Device Handler

1.  Login to the  [smarthings api](https://graph.api.smartthings.com/login/auth)
2.  Click on “My Device Handlers”
3.  Click on “+ New Device Handler”
4.  Select “From Code” Tab
5.  Paste code from Groovy/ST_Anything_DSC_Alarm.device.groovy file in the repo
6.  Click on “Create”
7.  Click on “Save”
8.  Click on “Public” -> “For Me”
9.  Click on “My Devices”
10.  Select your “Arduino ThingShield”
11.  Click on Edit
12.  Change type to “St_Anything_DSC_Alarm”  
    _It’s at the bottom of the list_
13.  Click on Update button
14.  Re-login to app on phone
15.  Click on the “Arduino ThingShield” thing  
    You should now see a bunch of tiles  
    _try a couple of doors/windows/pir sensors_  
    If all the tiles say open/motion you probably didn’t successfully pair the ThingShield
16.  Serial Monitor in Arduino should say joined now

# Verify that everything is working

1.  Open up the Arduino serial monitor  
    You should see a bunch of “Sending” events. If not check the jumpers from 2/3 to 14/15
2.  Every even corresponds to a switch or motion sensor

Table  
pirzone3 = Upstairs PIR  
pirzone2 = Downstairs PIR  
zone1 = 1st floor doors  
zone5 = Front bedroom windows  
zone4 = Front Living room windows

# Setup the multiplexer (Breaks out the sensors under the shield into separate virtual ones)

1.  In the API
2.  select "MySmartApps
3.  Select "+New SmartApp
4.  Click on Code tab
5.  Paste the Groovy/ST_Anything_DSC_Alarm/SmartApps/ST_Anything_Doors_Windows_Multiplexer.smartapp.groovy
6.  Click on “Create”
7.  Click on “Save”
8.  Click on “Public” -> “For Me”

# Create the Virtual Devices

## Create the handlers

1.  Select “My Device Handlers”
2.  Select “+Create New Device Handler”
3.  Select “From Code”
4.  Paste the Groovy/VirtualDevices/VirtualContactSensor.device.groovy
5.  Click on “Create”
6.  Click on “Save”
7.  Click on “Public” -> “For Me”
8.  Repeat for:  
    “VirtualMotionSensor.device.groovy”  
    “VirtualDoorControl.device.groovy”

## Create a device for each contact switch (You will be using)

1.  got to  `my devices`  in the api
2.  Click on new device
3.  Give it a unique name (Front Door etc…)
4.  Give it a random but unique device id
5.  “Type*” to “Virtual Contact Sensor” for the switches and Virtual PIM Sensor for the motion detectors
6.  . Set “Location” to Main House
7.  Set Hub to “Main House Hub”
8.  click on  **Create**
9.  Do this for each device! See above table for which and how many

## Add virtual devices to App

1.  From the SmartThings App, go to  **Marketplace -> SmartApps -> My Apps -> ST_Anything DSC Alarm Multiplexer**
2.  Pick a  `Zone 1`  (For the next sensor pick  `Zone 2`  etc…
3.  Select the  `1st Floor Doors`
4.  For all other zones select the  `Arduino ThingShield`  
    _all zones have to be set to something_
5.  For the device select "Arduino ThingShield`  
    Continue  [here](http://www.kendrickcoleman.com/index.php/Tech-Blog/total-noob-guide-to-move-your-old-wired-security-system-to-smartthings.html)

# Need to

Create virtual devices for each

# Customize for your house

1.  Edit the schetch  
    change the variables to match your zones

HTML 3146  characters 596  words 100  paragraphs
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc1NTgxMjAyOSwxMzQyMjM1NDE0LC0xOT
Y2MzU3NTU5LC0xOTY5NjAzMjczLC0yMTU5NTIyOTksLTEzNjE1
NDQ3NzQsMTExNDI4NTYyNSw3NDA1MzM3OTMsMTUwNzM2NTE2Ny
wxOTI2NjUwNTk1LC0xNTczMTM1NDM3LC01NzA4NTE0NzZdfQ==

-->