
1. Connect to the configuration samba share
	2. In osx in finder select "connect to server"
	3. put in the IP of the openhab box
	4. put in the user pass openhabian/openhabian
	5. Select `openHAB-conf` share
2. Load up the web ui
	3. http://IP:8080
	4. select paperUI (This does configuration
3. Disable simple mode (This seems to be the default for you)
	4. Configuration/System/Item Linking/Simple Mode (Off)
4. Setup network binding
	4. Select "Add-ons"
	5. Select "Bindings"
	6. Search for "Network Binding"
	7. Select "Install"
5. Add things
	5. Select "Inbox"
	6. Select "+"
	7. Select "Network Binding"
	8. From the list find your iphone (you can see your ip by clicking on wifi and info)
	9. Select the check
	10.Change the name to "James's Iphone"
6. Create links

# Zwave setup
1. Add the binding
	4. Select "Add-ons"
	5. Select "Bindings"
	6. Search for "Z-wave"
	7. Select "Install"
2. Configure the serial port
	3. Select Things
	4. Select Z-Wave Serial Controller
	5. Select z-wave
	6. Configure and specify /dev/ttyACM0 as the binding

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYzNjUxOTcxMCw1ODU3MzAyNjYsLTE3MT
IzMjcyMjEsNTUxNzMzMjI3LC02MTY4MzY3NiwxNjYyNjM3Nzg4
LC01MDE5MjQ4MTUsMjExOTg2NTMwLDg2OTI3NTM5Nyw3MzA5OT
gxMTZdfQ==
-->