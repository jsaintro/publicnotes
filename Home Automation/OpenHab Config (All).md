
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
	 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTUxNzMzMjI3LC02MTY4MzY3NiwxNjYyNj
M3Nzg4LC01MDE5MjQ4MTUsMjExOTg2NTMwLDg2OTI3NTM5Nyw3
MzA5OTgxMTZdfQ==
-->