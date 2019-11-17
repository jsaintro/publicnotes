

# HW Setup
You're using a Arduino MEGA256

# Arduino Setup

1.  Download the ST_anything project
    
    ```
    git clone https://github.com/DanielOgorchock/ST_Anything.git ST_Anything_Alarm
    cd ST_Anything_Alarm
    git checkout v2.9.7
    ```
2. Copy the multi sketch to your arduino directory
  Note: for Linux the DIR is ~/Arduino

   ```
   cp -r ST_Anything_Alarm/Arduino/Sketches/ST_Anything_Multiples_Thingshield/ ~/Arduino/Sketches/ST_Anything_Multiples_Thingshield
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
    -   Number of  "Button Devices" per garage relay/contact pair (2 by default)
    -  Note: If you visit the "Recently" page of your Parent Device in your ST App on your phone, you may get an annoying warning that the setup is not complete. If you've entered all of the required data above, you can safely ignore this message. Once it scrolls off the 'Recently' list, the pop-ups will stop.

1.  Once this is done you should see 2 buttons in the main things page (Rename and you're done)
#### Internal pull-up/-down resistors
GPIO 0-15 all have a built-in pull-up resistor, just like in an Arduino. GPIO16 has a built-in pull-down resistor.
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE1MzI1NDY3MV19
-->