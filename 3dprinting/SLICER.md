# SLICER install and setup

## Simplify 3D
Note: Before installing another copy of simplify 3d you'll have to deactivate the last instance.  The copy protection makes sure you only use the number you're licensed to use.  Deactivation can be done in your account or from inside the old program.

### Install
1.  Download from [here](https://www.simplify3d.com)
     Note: Check lastpass for login info
2. Unzip

        unzip Simplify3D-4.1.0-linux-x64-installer.zip 
3. Run installer as root

        sudo ./Simplify3D-4.1.0-linux-x64-installer.run

### Configure for use in gnome

1. Copy the desktop file to the right place

        sudo chown myuserid:myuserid ~/Desktop/Simplify3D.desktop
        chmod 600 ~/Desktop/Simplify3D.desktop
        mv ~/Desktop/Simplify3D.desktop ~/.local/share/applications/

### Configure
1. Configure firmware

     You're custom Wilson TS firmware is located on google drive [here](https://drive.google.com/file/d/1Gyy3sLMP8vbDZR3KGyHkDWy2GN9WNqof/view?usp=sharing)

2. Upload to simplify3d

3. Upload 


<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU0MjIxNzgzLDIwOTE1MzMwOTQsLTE1ND
kwMDE4NjhdfQ==
-->