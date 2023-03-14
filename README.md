# DIY-NAS
CEG2410 Project 2

1 - NFS Server Configuration
RAID previously created will be used 
It should automatically mount upon startup, if the fstab file is configured.

How to configure auto-mount:
Make sure the device is mounted:
sudo mount /dev/md0 /mnt/raid
Edit fstab!
sudo nano /etc/fstab
Add line:
/dev/md0  /mnt/raid  ext4  defaults  0  0
Unmount, remount, and test functionality
sudo umount /mnt/raid
sudo mount -a
mount
  
  
Installing NFS Server
Install Command
sudo apt-get install nfs-kernel-server
Create Shared Folder
mkdir ~/shared
Make the Folder Shared
sudo nano /etc/exports
~/shared 44.208.152.202(options)
Reload NFS Server
sudo exportfs -a
sudo systemctl restart nfs-kernel-server
  
  
Security Groups AWS
Leave outbound rules as default ALLOW
ALLOW https from any IPv4 address (can add IPv6)
ALLOW http from any IPv4 address (can add IPv6)
ALLOW ssh from "home" - public IP from ISP
ALLOW ssh from WSU - 130.108.0.0/16
ALLOW ssh within virtual network - 10.0.0.0/16
ALLOW nfs from "home" - public IP from ISP
ALLOW nfs from WSU - 130.108.0.0/16
ALLOW nfs within virtual network - 10.0.0.0/16
