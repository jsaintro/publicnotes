
# PrusaSlicer

## Linux
1. Download the appimage from [here]([https://github.com/prusa3d/PrusaSlicer/releases](https://github.com/prusa3d/PrusaSlicer/releases))
    
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
        #X-AppImage-Version=1.41.3+linux64.glibc2.14

3. Add to favorites

  1. Open activities window
  2. type `Prusa` into search window
  3. Right click on `Prusa Slicer` search result
  4. Select add to favorites


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMyMTAyNTk0LC0xODEzOTk1MTMsMTQyMz
kzMTgxNiwxNDA5NTkzODE1LC0zOTYwNjQwODUsODcwOTAwMjc1
LDM5NzI0OTEwLDMzOTAzOTAxOCwtMTM1MjA4MDgxOV19
-->