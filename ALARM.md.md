# HW Setup
1. Attach the smartthings sheild to the arduino
   Note: Match up the pin labels between the two boards.
1. Setup the alternate serial pins
   jumper pin 2 -> 14 (tx3)
   jumper pin 3 -> 15 (rx3)
   set switch on shield to D2/D3
   Note: This allows you to troubleshoot using the serial monitor
   also this is the only way i've gotten everything to work


# Arduino Setup

1. Download the ST_anything project

        git@github.com:jsaintrocc/ST_Anything.git

2. Copy the Sketches and Libraries folders from the project in the Arduino directory

3. Open the Arduino App and load the ST_Anything_DSC_Alarm Sketch

        Arduino/Sketches/ST_Anything_DSC_Alarm/ST_Anything_DSC_Alarm.ino
5. Compile the sketch
   (The check icon)
6. Upload the compiled sketch to the Arduino

# Pairing SmartThings shield with hub
1. Power on the Arduino with shield attached
2. Put it into pairing mode (If it's been paired before)
    Hold the `switch` button for 6 seconds (Red light should come on)
4. In the App go into pairing mode looking for a device
5. Hit the "switch" button on the shield (Unless you already did the 6 second hold ???)
6. Should pair as an Arduino ThingShield

# Setup the Device Handler
1. Login to the [smarthings api](https://graph.api.smartthings.com/login/auth)
1. Click on "My Device Handlers"
1. Click on "+ New Device Handler"
1. Select "From Code" Tab
1. Paste code from Groovy/ST_Anything_DSC_Alarm.device.groovy file in the repo
1. Click on "Create"
1. Click on "Save"
1. Click on "Public" -> "For Me"
1. Click on "My Devices"
1. Select your "Arduino ThingShield"
1. Click on Edit 
1. Change type to "St_Anything_DSC_Alarm"
   *It's at the bottom of the list*
1. Click on Update button
1. Re-login to app on phone
1. Click on the "Arduino ThingShield" thing
   You should now see a bunch of tiles
1. Serial Monitor in Arduino should say joined now
# Verify that everything is working
1. Open up the Arduino serial monitor
   You should see a bunch of "Sending" events.  If not check the jumpers from 2/3 to 14/15
2. Every even corresponds to a switch or montion sensor

Table
pirzone3 = Upstairs PIR
pirzone2 = Downstairs PIR
zone1 = 1st floor doors
zone5 = Front bedroom windows
zone4 = Front Living room windows

# Setup the multiplexer (Breaks out the sensors under the shield into separate virtual ones)
1. In the API
1. select "MySmartApps
1. Select "+New SmartApp
1. Click on Code tab
1. Paste the Groovy/ST_Anything_DSC_Alarm/SmartApps/ST_Anything_Doors_Windows_Multiplexer.smartapp.groovy
1. Click on "Create"
1. Click on "Save"
1. Click on "Public" -> "For Me"

# Create the Virtual Devices
## Create the handlers
1. Select "My Device Handlers"
1. Select "+Create New Device Handler"
1. Select "From Code"
1. Paste the Groovy/VirtualDevices/VirtualContactSensor.device.groovy
1. Click on "Create"
1. Click on "Save"
1. Click on "Public" -> "For Me"
1. Repeat for:
  "VirtualMotionSensor.device.groovy"
  "VirtualDoorControl.device.groovy"
## Create a device for each contact switch (You will be using)

1. got to `my devices` in the api
2. Click on new device
3. Give it a unique name (Front Door etc...)
4. Give it a random but unique device id
5. "Type*" to "Virtual Contact Sensor"
6. . Set "Location" to Main House
7. Set Hub to "Main House Hub"
8.  click on **Create**
9. . Do this for each device! If you have 13 devices, then make 13.
Continue [here](http://www.kendrickcoleman.com/index.php/Tech-Blog/total-noob-guide-to-move-your-old-wired-security-system-to-smartthings.html)
# Need to 
Create virtual devices for each 

# Customize for your house
1. Edit the schetch
   change the variables to match your zones
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTA5MjM1NTIwLDI4NTA1NjUxNSwtMTIyNj
k4MTc1NywxMTM4NTE5NzgxLC0xMjU4NDg0MzUxLC05NzMzNDgx
MTAsMTczODc3Mjc2MCwtMTg1ODM2NTAxOF19
-->