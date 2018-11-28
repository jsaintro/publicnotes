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

4. Add user permissions for your account

        myuserid@myhost:~$ /opt/Simplify3D-4.1.0/AddUserPermissons.sh

### Configure for use in gnome

1. Copy the desktop file to the right place

        sudo chown myuserid:myuserid ~/Desktop/Simplify3D.desktop
        chmod 600 ~/Desktop/Simplify3D.desktop
        mv ~/Desktop/Simplify3D.desktop ~/.local/share/applications/

### Configure
1. Import your custom firmware
	1. Download custom firmware from google drive [here](https://drive.google.com/file/d/1Gyy3sLMP8vbDZR3KGyHkDWy2GN9WNqof/view?usp=sharing)

    2. Import

        "Tools/Firmware Configuration/Import/WilsonTS.frm"
    
1. Import FFF profiles
	1. Download all `.fff` files from google drive [here](https://drive.google.com/drive/u/0/folders/1Wc8FOE6dGREPz78OsDsMViDP6AQq866M)

    2. Import

        "File/Import FFF Profile/*.fff"


4. Upload 


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzAyNTEyNjAsMzU0MjIxNzgzLDIwOT
E1MzMwOTQsLTE1NDkwMDE4NjhdfQ==
-->