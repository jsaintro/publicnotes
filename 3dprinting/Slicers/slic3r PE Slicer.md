
# PrusaSlicer

## Linux
1. Download the appimage from [Here](https://github.com/prusa3d/PrusaSlicer/releases)
    
        user@workstation:~$ mkdir PrusaSlicer
        user@workstation:~$ cd PrusaSlicer
        user@workstation:~$ wget https://github.com/prusa3d/PrusaSlicer/releases/download/version_2.1.1/PrusaSlicer-2.1.1+linux64-201912101511.AppImage
        user@workstation:~$ chmod +x PrusaSlicer-2.1.1+linux64-201912101511.AppImage
2. Run

        user@workstation:~$ ./PrusaSlicer-2.1.1+linux64-201912101511.AppImage

## Make Desktop Icon
1. Download the slic3r icon image

        wget https://github.com/prusa3d/PrusaSlicer/raw/master/resources/icons/PrusaSlicer.png

2. Create the gnome desktop file

        vi ~/.local/share/applications/PrusaSlicer.desktop
        [Desktop Entry]
        Name=PrusaSlicer
        Exec=/home/jsaintrocc/PrusaSlicer/PrusaSlicer-2.1.1+linux64-201912101511.AppImage
        Icon=/home/jsaintrocc/PrusaSlicer/PrusaSlicer.png
        Terminal=false
        Type=Application
        Categories=Graphics;3DGraphics;
        
3. Add to favorites

  1. Open activities window
  2. type `Prusa` into search window
  3. Right click on `PrusaSlicer` search result
  4. Select add to favorites

## Updating
1. Copy the .Prusaslicer directory
2. export the config
3. export the configbundle
Download the app image

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQzNzQxNDU5NSwtODEwMTQwMDQ0LDQ2Nz
kyMDE4MCwtMzIxMDI1OTQsLTE4MTM5OTUxMywxNDIzOTMxODE2
LDE0MDk1OTM4MTUsLTM5NjA2NDA4NSw4NzA5MDAyNzUsMzk3Mj
Q5MTAsMzM5MDM5MDE4LC0xMzUyMDgwODE5XX0=
-->