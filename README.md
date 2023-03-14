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
