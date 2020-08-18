

Install instructions sourced from here
[https://www.openhab.org/docs/installation/openhabian.html](https://www.openhab.org/docs/installation/openhabian.html)

## Imaging
1. Download the image
[https://github.com/openhab/openhabian/releases](https://github.com/openhab/openhabian/releases)
2. uncompress the xz file
```
xz -d openhabian-pi-raspbian....img.xz
```
Note: brew install xz if you don't have it. Note try just useing the xz file with etcher next time
3. Use balenaetcher to write the image to a Sd card

## Initial Boot
1. Connect wired ethernet
2. Connect HDMI monitor (Isn't required but can be convenient to see where you are
3. Insert SD Card
4. Add Power
5. Will take about 30 minutes?
6. You can watch the progress at http://openhab/ this will shutdown when it's done
## Web Setup
1. Access the Web Interface
http://openhab:8080
2. Select "Standard"
## Samba Shares
username openhabian Password openhabian
## Log Viewer
http://openhab:9001
## SSH
ssh openhabian@openhab
user: openhabian pass:openhabian


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTI4NDAyMTIsLTE2NTkxNzUwMTQsMT
E2MTEzNTQ4OSwtMTI2NTU4NTg2M119
-->