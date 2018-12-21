## Installing

### Ubuntu 18.10
Note: Currently no package in the main repos to install nightly

1. Install the apt key

        wget -qO - http://files.openscad.org/OBS-Repository-Key.pub | sudo apt-key add -

2. Install the nightly repo

         vi /etc/apt/sources.list.d/openscad.list
         deb http://download.opensuse.org/repositories/home:/t-paul/xUbuntu_18.10/ ./

3. Install the package

        apt-get install openscad-nightly
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMDAyMDkzMjJdfQ==
-->