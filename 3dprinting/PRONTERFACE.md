# Pronterface Notes
Pronterface lets you control your 3dprinter via the usb

## Install
Note: Don't use the Ubuntu package it's buggy

1. Install the dependencies:
    ```
    sudo apt install python3-serial python3-numpy cython3 python3-libxml2 python3-gi python3-dbus python3-psutil python3-cairosvg libpython3-dev python3-appdirs python3-wxgtk4.0

    ```

    ```
    sudo apt install python3-pip
    pip3 install --user pyglet

     ```

2. Clone the printrun repository:
    ```
    cd ~
    git clone https://github.com/kliment/Printrun.git
    cd Printrun
    ```

3. Checkout latest tagged release

       git tag -l
       git checkout printrun-2.0.0rc7

5. Run

       ./pronterface.py

## Gnome Setup
2. Create the gnome configuration file

        vi ~/.local/share/applications/pronterface.desktop
        [Desktop Entry]
        Type=Application
        Name=Pronterface
        GenericName=Printer Interface
        Comment=Controls your 3D printer
        Icon=/home/<<username>>/Printrun/pronterface.ico
        Exec=/home/<<username>>/Printrun/pronterface.py %f
        Path=/home/<<username>>/Printrun/
        StartupNotify=true
        Terminal=false
        Categories=GNOME;GTK;Utility;Graphics;3DGraphics;
        MimeType=application/sla;model/x.stl-binary;model/x.stl-ascii;text/x.gcode;

3. You can now search and use pronterface like any other application and also make a favoriate out of it

## Upgrading
1. View the latest tag

       cd ~/Printrun
       git fetch
       git tag -l

2. Checkout the latest tag

       git checkout printrun-2.0.0rc7
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDc2NDgwODI0LDk4NDM1OTg5NCwxNjA4MT
IyNTMyLC0xNDY3ODgyNDI4LC0xNzI1MzUzNTM5LC02ODgwMjk2
MjEsMTA1MzgyODAyMSwtMTc3MjMzMjQ5MywxMzI0MTMwNTYwXX
0=
-->