## Making a boot disk
1. Download pop os from https://system76.com/pop
2. Download Etcher from https://www.balena.io/etcher/
3. Make the USB boot disk using etcher
4. Boot the USB boot disk F2 for BIOS F7 for boot menu
5. Install Pop OS
    1. Use full disk encryption as it's got better performance that home folder encryption
6. Setup dual monitors
    1. By default 2nd monitor is turned off (Activities/Displays)
7. Do a system update

        sudo apt update
        sudo apt dist-upgrade
        sudo reboot
        
8. Setup Lastpass for firefox
    1.  In firefox add-ons select lastpass
9. Install commercial Chrome (Not Chromium)
    1.  Download from https://www.google.com/chrome/browser
10. Setup Lastpass for Chrome
	1. chrome://extensions
	2. open the chrome web store
	3. search for lastpass
11. Test netflix
12. Test youtube
13. Upgrade system76 firmware
    9. Actions/System76 Firmware updater
        Note: Make sure ALL USB and external displays are disconnected
        Note: There's a scary moment when the system shuts down completely.
        Just wait a minute and then start with button

14. install gnome extensions
	15. https://extensions.gnome.org
	16. Dash to Dock
	17. CPU Power Manager
	18. Multi Monitors Add-On
15. Add the printer (Built in driver works fine)

## Misc

Add some libs that stuff requires
etcher complains about this one
sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module


  
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjU2NDA1ODIsLTE0MzYwNjA5MDUsMjA5MD
c2NTM4MywxMzI1MjU1MjUwLC05MDkwOTE3OTUsLTE1MDUzNjM4
NTYsMjA5ODc2ODU3NCwtMTg5NTQyODQzOSwtNjU4MzIxNTY0LC
0xODU3NTkyODQwLDIxMjM2NjA0MTUsMTY1NzUyOTA1NiwtNzY0
NDc1MDQzLC0yMDE2NDQxOTY1LDQxNzU3ODg2MywtMTQ0MDMxMD
gzNSwtMTYwMjM3NzkyNywzMDU3MzgwMTZdfQ==
-->