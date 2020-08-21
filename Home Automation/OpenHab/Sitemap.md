


1. Connect to openHAB-conf samba share
2. create some default files
```
DCSML-1584768:items jsaint201$ touch items/default.items
DCSML-1584768:items jsaint201$ touch sitemaps/default.sitemap
```

3. create some default items
Switch Presence_Mobile_James "James's Iphone" <presence> { channel="network:device:192_168_86_37:online" }
Switch Wallplug_FF_LR_Lamp "Living Room Lamp" <poweroutlet> { channel="zwave:device:93caa54f:node4:switch_binary" }

Channel is the important bit you can find that out in paperUI
```
ItemType ItemName "ItemDescription" <ItemIcon> { ItemToThingChannelLink }
```
icons are here
[https://www.openhab.org/docs/configuration/iconsets/classic/](https://www.openhab.org/docs/configuration/iconsets/classic/)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc0MjU4NjMzMyw2Nzc4NzY5OTgsLTE1ND
E3MzY4MzldfQ==
-->