# DIY-NAS
CEG2410 Project 2

# 1 - NFS Server Configuration  

RAID previously created will be used.  

It should automatically mount upon startup, if the fstab file is configured.  

- How to configure auto-mount:  

- Make sure the device is mounted:  

```sudo mount /dev/md0 /mnt/raid```  

- Edit fstab!  

```sudo nano /etc/fstab```  

- Add line:  

```/dev/md0  /mnt/raid  ext4  defaults  0  0```  

- Unmount, remount, and test functionality  

```sudo umount /mnt/raid```  

```sudo mount -a```  

```mount```  
  
![broken image](tree/main/img/mounted.PNG "Mounted")  


# 2 - Installing NFS Server
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
  
  
# 3 - Security Groups AWS
Leave outbound rules as default ALLOW
ALLOW https from any IPv4 address
ALLOW http from any IPv4 address
ALLOW ssh from home
ALLOW ssh from WSU
ALLOW ssh within virtual network
ALLOW nfs from home
ALLOW nfs from WSU
ALLOW nfs within virtual network
  
  
# 4 - Mounting an NFS Share
Install NFS in WSL2
Install command
sudo apt-get install nfs-common
Create NFS Mount Point
mkdir ~/nfs
Mount NFS Share
sudo mount -t nfs host.docker.internal:/path/to/shared/folder ~/nfs
Test
echo "Hello, NFS!" > ~/nfs/hello.txt
