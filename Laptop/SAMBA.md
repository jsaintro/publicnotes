## Fix for the SAMBA share on the RT-AC1900

1. install samba client

        apt install smbclient

2. Revert to old authentication method

        vi /etc/samba/smb.conf
        [global]
        # Fix for Asus RT-AC1900 samba share
           client NTLMv2 auth = no
           client use spnego = no

3. Test

        smbclient //storageserver/storage -U username

   Note: Check lastpass ASUS entry for details

4.  Samba access should now work for nautilus as well
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3NzkzNjMyLDE0NDA2MzU1NDYsNDM2Mj
U2NjA0XX0=
-->