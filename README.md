# Arch_Linux_Installation
Simple Arch Linux Installation  (according to me ) 


#SET FONT BIGGER
1. setfont /usr/share/kbd/consolefonts/sun12X22.psfu.gz

#CHECK UEFI IS ENABLE OR NOT
2. ls /sys/firmware/efi/efivars

#CHECK WIFI ROUTER IS SHOWN OR NOT
3. ip link

#CONNECT USING WIFI
4.    iwctl
   -> station wlan0 connect "POCO M2 PRO"
   -> (enter password of your SSID)
   -> exit

#CHECK INTERNET IS WORKING OR NOT
5. ping -c 4 google.com

#DISK PARTITION 
6.    fdisk -l
   -> fdisk /dev/sdb              #YOUR PARTITION NAME
    -> n                          #FOR NEW PARTITION
   -> first sector (DEFAULT)      
   -> last sector  (+512M)        #512 MB SPACE FOR EFI PARTITION                        
   -> t                           #TO CHANGE ITS TYPE
   -> set 1                       #1 IS FOR EFI PARTITION
   -> n                           #FOR NEW PARTITION
   -> first sector (DEFAULT)
   -> last sector  (+40G)         #40 GB FOR ROOT STORAGE
   -> n                           #FOR NEW PARTITION
   -> first sector (DEFAULT)
   -> last sector  (+50G)         #50GB FOR HOME DIRECTORY
   -> n                           #FOR NEW PARTITION
   -> first sector (DEFAULT)
   -> last sector  (DEFAULT)
   -> t                           #TO CHANGE TYPE
   -> set 19                      #19 FOR SWAP PARTITION
   -> p                           #TO SHOW ALL PARTITION IS ARRANGE ACCORDINGLY
   -> w                           #WRITE CHANGES TO DISK 
                                  (PLEASE TRIPE CHECK YOUR PARTITION THEN RUN THIS COMMAND AS THERE IS HIGN CHANGE THAT YOU RUINED YOUR DISK)
                                  
                                  Name 	  Partition 	Size 	        Type
                                  sdb4 	  /efi  	    512M 	        EFI
                                  sdb5 	  /           64G 	        ext4
                                  sdb6 	  swap 	      16G 	        swap
                                  sdb7 	  /home 	(Remaining space) ext4
                                  
 #FORMAT PARTITION 
 7.  
     mkfs.fat -F32 -n EFI /dev/sdb4   #FOR EFI PARTITION
     mkfs.ext4 /dev/sdb5              #FOR ROOT PARTITION
     mkfs.ext4 /dev/sdb6              #FOR HOME PARTITION
     mkswap /dev/sdb7                 #FOR SWAP PARTITION
     swapon /dev/sdb7
 
                                  
 #MOUNT PARTITION
 8. 
    mount /dev/sdb5 /mnt
    mount /dev/sdb6 /mnt/home
    mkdir /mnt/efi
    mount /dev/sda2 /mnt/efi  (NOTE HERE SDA2 IS WINDOWS EFI PARTITION)
    
#INSTALL BASIC LINUX BASE PACKAGES
9. pacstrap /mnt base linux linux-firmware

#GENERATE FSTAB
10. genfstab -U /mnt >> /mnt/etc/fstab

#IN /MNT ROOT DIRECTORY
11.      arch-chroot /mnt
      -> pacman -Sy nano
      -> nano /etc/locale.gen  (UNCOMMENT en_IN )
      -> locale-gen
      -> echo "LANG=en_IN.UTF-8" > /etc/locale.conf
      -> ln -sf /usr/share/zoneinfo/Asia/Kolkata /etc/localtime
      -> timedatectl set-ntp true
      -> timedatectl status
      -> hwclock --systohc
      -> date
      -> echo kingcoolvikas > /etc/hostname
      -> nano /etc/hosts 
      
          127.0.0.1     localhost
          ::1           localhost
          127.0.1.1     kingcoolvikas.localdomain   kingcoolvikas
          
          
          ((( INCOMPLETE  )))
        
      
      
      
      
      
      
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   

