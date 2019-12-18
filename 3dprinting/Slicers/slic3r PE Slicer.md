
# PrusaSlicer

## Linux
1. Download the appimage from [here]([https://github.com/prusa3d/PrusaSlicer/releases](https://github.com/prusa3d/PrusaSlicer/releases))
    
        user@workstation:~$ mkdir PrusaSlicer
        user@workstation:~$ cd PrusaSlicer
        user@workstation:~$ wget https://github.com/prusa3d/PrusaSlicer/releases/download/version_2.1.1/PrusaSlicer-2.1.1+linux64-201912101511.AppImage
        user@workstation:~$ chmod +x PrusaSlicer-2.1.1+linux64-201912101511.AppImage
2. Run

        user@workstation:~$ ./PrusaSlicer-2.0.0+linux64-201905201652.AppImage

## Make Desktop Icon
1. Download the slic3r icon image

        wget https://github.com/prusa3d/Slic3r/raw/master/resources/icons/Slic3r.png

2. Create the gnome desktop file

        vi .local/share/applications/slic3rPE.desktop
        [Desktop Entry]
        Name=Prusa Slicer
        Exec=/home/jsaintrocc/slic3rPE/Slic3rPE-1.41.3+linux64-full-201902121303.AppImage
        Icon=/home/jsaintrocc/slic3rPE/Slic3r.png
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
eyJoaXN0b3J5IjpbMTQ0NDAwMTE4NCwxNDIzOTMxODE2LDE0MD
k1OTM4MTUsLTM5NjA2NDA4NSw4NzA5MDAyNzUsMzk3MjQ5MTAs
MzM5MDM5MDE4LC0xMzUyMDgwODE5XX0=
-->