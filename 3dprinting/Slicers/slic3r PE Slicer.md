
# PrusaSlicer

## Linux
1. Download the appimage from [Here](https://github.com/prusa3d/PrusaSlicer/releases)
    
        user@workstation:~$ mkdir PrusaSlicer
        user@workstation:~$ cd PrusaSlicer
        user@workstation:~$ wget https://github.com/prusa3d/PrusaSlicer/releases/download/version_2.1.1/PrusaSlicer-2.1.1+linux64-201912101511.AppImage
        user@workstation:~$ chmod +x PrusaSlicer-2.1.1+linux64-201912101511.AppImage
2. Run

        user@workstation:~$ /PrusaSlicer-2.1.1+linux64-201912101511.AppImage

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


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgxMDE0MDA0NCw0Njc5MjAxODAsLTMyMT
AyNTk0LC0xODEzOTk1MTMsMTQyMzkzMTgxNiwxNDA5NTkzODE1
LC0zOTYwNjQwODUsODcwOTAwMjc1LDM5NzI0OTEwLDMzOTAzOT
AxOCwtMTM1MjA4MDgxOV19
-->