# Arch Linux Installation

**Simple Arch Linux Installation  (according to me )** 

 SET FONT BIGGER
* setfont /usr/share/kbd/consolefonts/sun12x22.psfu.gz

 CHECK UEFI IS ENABLE OR NOT
* ls /sys/firmware/efi/efivars

## CHECK WIFI ROUTER IS SHOWN OR NOT
* ip link

## CONNECT USING WIFI
* iwctl
* station wlan0 connect "POCO M2 PRO"
* (enter password of your SSID)
* exit

## CHECK INTERNET IS WORKING OR NOT
* ping -c 4 google.com

## DISK PARTITION 
*  fdisk -l
*  fdisk /dev/sdb              
*  n                           
*  first sector (DEFAULT)      
*  last sector  (+512M)                               
*  t                          
*  set 1                       
*  n                           
*  first sector (DEFAULT)
*  last sector  (+40G)         
*  n                           
*  first sector (DEFAULT)
*  last sector  (+50G)         
*  n                           
*  first sector (DEFAULT)
*  last sector  (DEFAULT)
*  t                           
*  set 19                      
*  p                          
*  w                            
*  **(PLEASE TRIPE CHECK YOUR PARTITION THEN RUN THIS COMMAND AS THERE IS HIGN CHANGE THAT YOU RUINED YOUR DISK)**
      
      
      
      
      
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   

