
# Slic3r PE Install

## Linux
1. Download the appimage from [here](https://github.com/prusa3d/Slic3r/releases/tag/version_1.41.3)
    
        user@workstation:~$ mkdir slic3rPE
        user@workstation:~$ cd slic3rPE
        user@workstation:~$ wget https://github.com/prusa3d/Slic3r/releases/download/version_1.41.3/Slic3rPE-1.41.3+linux64-full-201902121303.AppImage
        user@workstation:~$ chmod +x Slic3rPE-1.41.3+linux64-full-201902121303.AppImage
2. Run

        user@workstation:~$ ./Slic3r-1.3.0-x86_64.AppImage

## Make Desktop Icon
1. Download the slic3r icon image

        wget https://github.com/prusa3d/Slic3r/raw/master/resources/icons/Slic3r.png

2. Create the gnome desktop file

        vi .local/share/applications/slic3rPE.desktop
        [Desktop Entry]
        Name=Slic3r Prusa Edition
        Exec=/home/jsaintrocc/slic3rPE/Slic3rPE-1.41.3+linux64-full-201902121303.AppImage --gui
        Icon=/home/jsaintrocc/slic3rPE/Slic3r.png
        Terminal=false
        Type=Application
        Categories=Graphics;3DGraphics;
        X-AppImage-Version=1.41.3+linux64.glibc2.14


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3MDY2MDAxMCwzOTcyNDkxMCwzMzkwMz
kwMTgsLTEzNTIwODA4MTldfQ==
-->