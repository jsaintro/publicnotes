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
5. http://arduino.esp8266.com/stable/package_esp8266com_index.json
6. Now open up the board and click the board manager at the bottom you should be able to install the esp8266 lib now
7. 
~/Arduino/ST_Anything_GarageDoor_ESP8266WIFI
  ST_Anything_Garage/Arduino/Sketches/ST_Anything_GarageDoor_ESP8266WIFI
8.  Copy the Sketches and Libraries folders from the project in the Arduino directory
-   Download the ST_Anything repository, focusing on the ST_Anything/Arduino/ folders
-   This folder structure should mirror that of your local User Arduino directory.
    -   On Mac, it's located in  `~/Documents/Arduino/`.
    -   On Windows, it's located in  `C:\Users\yourusername\Documents\Arduino`.
-   Look inside the  `Arduino/Sketches`  folder of the repo.
-   Copy and paste all of the  `ST_Anything_...`  sketch folders into your local Arduino sketches directory. If you haven't created any sketches, you may not see the folder. In this case, feel free to create it.
-   Look inside the  `Arduino/libraries`  folder of the repo.
-   Copy and paste both the  `ST_Anything...`  and  `SmartThings...`  folders (as well as ALL of the other library folders) into your local Arduino libraries directory.
-   Open one of the ST_Anything_Multiples_xxxxx.ino sketches for the hardware you're using and see if it successfully compiles.
    -   Make sure you select the correct model of board you are compiling for.
    -   If building for a standalone ESP8266 board, make sure you have configured the Arduino IDE to include support for these boards. Follow the guide at  [https://learn.sparkfun.com/tutorials/esp8266-thing-hookup-guide/installing-the-esp8266-arduino-addon](https://learn.sparkfun.com/tutorials/esp8266-thing-hookup-guide/installing-the-esp8266-arduino-addon)
    ```
    
    
9.  Open the Arduino App and load the ST_Anything_DSC_Alarm Sketch
    
    ```
     Arduino/Sketches/ST_Anything_DSC_Alarm/ST_Anything_DSC_Alarm.ino
    
    ```
    
10.  Compile the sketch  
    (The check icon)
    
11.  Upload the compiled sketch to the Arduino
    

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
eyJoaXN0b3J5IjpbMTIzNzc0NDAxNiwxNTA3MzY1MTY3LDE5Mj
Y2NTA1OTUsLTE1NzMxMzU0MzcsLTU3MDg1MTQ3Nl19
-->