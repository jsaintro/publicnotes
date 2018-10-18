
First Boot any linux live cd  

Code:

Otherwise the dd command will dump the bits of even the files that where previously deleted.  
  
Empty out the unused blocks of your hard disk with zeros, using command:  
  

Code:

Unmount the source file system  
  

Code:

  
Create the compressed image:  
  
From a terminal change directory to the folder in your external usb drive or NFS volume where you want to dump the backup  
  

Code:

It will create 2GB files in this fashion:  
  
system_drive_backup.img.gz.aa  
system_drive_backup.img.gz.ab  
system_drive_backup.img.gz.ac  
...  
etc, etc  
  
  
"dd" is the command to make a bit-by-bit copy of "if=/dev/sda" as the "Input File" to "of=/mnt/sda1/sda.img.gz" as the "Output File". Everything from the partition will go into an "Output File" named "sda.img.gz". "conv=sync,noerror" tells dd that if it can't read a block due to a read error, then it should at least write something to its output of the correct length. Even if your hard disk exhibits no errors, remember that dd will read every single block, including any blocks which the OS avoids using because it has marked them as bad. "bs=64K" is the block size of 64x1024 Bytes. Using this large of block size speeds up the copying process. The output of dd is then piped through gzip to compress it and in turn piped to split in order to split it in 2gb chunks which fit nicely on FAT32 drives  
  
  
  
To restore the image:  

Code:

[edit]  
Storing extra information about the drive geometry necessary in order to interpret the partition table stored within the image  

Code:

NOTE: I do not claim credit for this, I have just put together this stuff from info on the web

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI1MDg0MzIzXX0=
-->