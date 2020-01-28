# Pronterface Notes
Note: printrun project is dead.  Should probably find an alternative at some point.

pronterface lets you control your 3dprinter via the usb

1. Install

Note: Don't use the Ubuntu package it's buggy

Install the dependencies:

```
sudo apt install python3-serial python3-numpy cython3 python3-libxml2 python3-gi python3-dbus python3-psutil python3-cairosvg libpython3-dev python3-appdirs python3-wxgtk4.0

```

```
sudo apt install python3-pip
pip3 install --user pyglet

```

Install git, clone this repository:

```
cd ~
git clone https://github.com/kliment/Printrun.git
```

2. Run

         ./pronterface.py
## Gome Setup
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

4. You can now search and use pronterface like any other application and also make a favoriate out of it
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwODEyMjUzMiwtMTQ2Nzg4MjQyOCwtMT
cyNTM1MzUzOSwtNjg4MDI5NjIxLDEwNTM4MjgwMjEsLTE3NzIz
MzI0OTMsMTMyNDEzMDU2MF19
-->