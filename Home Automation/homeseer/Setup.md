Get a trial license for rpi
Once your order processes you need to go to the invoice on the web to see your trial license id/pw

in the email link download the software
Note the pdf instruction they provided are in https://drive.google.com/drive/folders/1m_vBEfAGRF5KHUhow7n0Gjo8DtMLx9Zt?usp=sharing

ONce flashed you have to hardware device initially

Once registered here is the quick start guide
youtube.com/watch?v=Q4L4FFwA7Gc

1. Register a myhs account
2. https://myhs.homeseer.com/ click register note: lastpass myhs.homeseer.com (This is different than the shop account)

## Z-Wave Setup
1. Enabled the plugin
    `Plugins/Installed/Z-Wave/Enable`
2. Add the smartstick controller
    `Plugins/Z-Wave/Controller Management`
    `Add Interface`
    Name: SmartStick+
    Interface Model: HomeSeer SmartStick +
    Serial Port: /dev/ttyACM0

3. Enable the interface

### Add the Outdoor switch
1. Manage Z-Wave Controller
`Plugins/Z-Wave/Controller Management`
2. Start Include Mode
`Expand Z-Wave Interfaces\Actions:\Add\Include Node
3. Toggle outdoor switch to include it.



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyMDg0NDkzMywxOTU0MTE5MDY5LDEzOT
EzOTAxNDMsLTE3MjE0ODA4MzAsNzI5MjcxNTU0LC0xOTcxNTkw
MDU1LDE2NjM2ODMzNDksODkzNDI0MzQ2LDM2NzUzOTIxMF19
-->