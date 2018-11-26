# Pronterface Notes
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
sudo apt install git
git clone https://github.com/kliment/Printrun.git
cd Printrun

```
2. Run

         ./pronterface.py
## Gome Setup
1. Copy the source to opt
        sudo cp Printrun /opt
2. Create the gnome configuration file
        vi ~/.local/share/applications/pronterface.desktop
        

4. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0Mjc2NDk0MSwxMDUzODI4MDIxLC0xNz
cyMzMyNDkzLDEzMjQxMzA1NjBdfQ==
-->