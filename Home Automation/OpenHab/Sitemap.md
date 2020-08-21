


1. Connect to openHAB-conf samba share
2. create some default files
```
DCSML-1584768:items jsaint201$ touch items/default.items
DCSML-1584768:items jsaint201$ touch sitemaps/default.sitemap
```

3. create some default items
Switch Presence_Mobile_James "James's Iphone" <presence> { channel="network:device:192_168_86_37:online" }
Switch Wallplug_FF_LR_Lamp "Living Room Lamp" <poweroutlet> { channel="zwave:device:93caa54f:node4:switch_binary"}

Channel is the important bit you can find that out in paperUI
```
ItemType ItemName "ItemDescription" <ItemIcon> { ItemToThingChannelLink }
```
icons are here
[https://www.openhab.org/docs/configuration/iconsets/classic/](https://www.openhab.org/docs/configuration/iconsets/classic/)

4. Create the sitemap
sitemap default label="My first sitemap"
{
    Switch item=Presence_Mobile_James label="James's Iphone"
    Switch item=Wallplug_FF_LR_Lamp label="Living Room Lamp"
}

The important part is the item= which associates it with the item defined in the items table
desc is arbitrary

5. Configure Basic UI to use default sitemap
	6. go into paperUI
	7. Select services/UI
	8. Select Configure for BasicUI
	9. Under "Default Sitemap" specify "default"
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyODMwNTE5OSwtNzQyNTg2MzMzLDY3Nz
g3Njk5OCwtMTU0MTczNjgzOV19
-->