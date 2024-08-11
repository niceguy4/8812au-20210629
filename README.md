### Credit: https://www.youtube.com/watch?v=Yr-8RmoNi70&t and whoever made 8812au-20210629-main

### Device: ALFA AWUS036ACH - https://www.amazon.com/dp/B08SJC78FH

### Chipset: Realtek RTL8812AU 

### Kali: 2024.2

### Issue: 
  * Device not showing up in Kali Linux. It may show up in LSUSB but not in IW DEV or IWCONFIG
    
  * And/or, device shows up Kali in IW DEV and IWCONFIG but adapter does not collect/capture clients when using wifite or airodump-ng
    
  * Current vendor, aircrack-ng and morrownr driver updates don't resolve issue as of 8/11/2024

### Steps: 
Setup was tested on Windows 11 running Kali (kali-linux-2024.2-vmware-amd64) virtual machine using VMWare (17.5.0 build-22583795). Kali in VirtualBox (7.0.20) works, too (kali-linux-2024.2-virtualbox-amd64) as of 8/11/2024. Prior to this fix below, the wireless adapter worked in Windows 11 and it showed networks and will connect to networks in Windows 11 but the wirelesss adapter did not work in Kali.

1. First, assuming you have ethernet, unplug USB wireless adapter and uninstall the Windows drivers for Realtek RTL8812AU including the utility app.
   
2. Restart computer and then plug USB wireless adapter back into USB slot. Mmake sure the blue light blinks on the wireless adapter or move to another USB slot.

3. Go to Windows Device Manager, right click on the adapter under Network Adapters, Update Driver, Search automatically for Drivers. Restart computer.

   ![pray](https://raw.githubusercontent.com/niceguy4/8812au-20210629/main/device_manager.png)

4. Load Kali in VMWare or Virtualbox.

5. And then follow intructions from https://www.youtube.com/@ka3boosh48 . Note, I've included the driver file in github in case mediafire link goes down.

```
be sure to remove all the drivers before you follow the steps to avoid any error 

for new installation of kali linux 2024.2

first you need to add the sources file
nano /etc/apt/sources.list
add
deb http://http.kali.org/kali kali-last-snapshot main contrib non-free
deb http://http.kali.org/kali kali-experimental main contrib non-free

Next
apt-get update && apt upgrade ( the system will install kali image and kernal 6.8.11

Next search for linux-headers
apt install linux-headers-$(uname -r | sed 's,[^-]*-[^-]*-,,')
hit inter the system will download kali-headers for 6.8.11

Next copy the zip file and extract it ( see the video )
Download the driver file from here
www.mediafire.com/file/tuyze3vc65zckne/8812au-20210629-main.zip/file (or download github here)

open terminal 
inter this command 
sudo apt-get install bc mokutil build-essential libelf-dev linux-headers-`uname -r`

Next 
sudo ./install-driver.sh
after its done click N then Y then reboot the system 
you are good to go your ALFA awus036ach ac1200 will be working without any issue 

if this fix your issue please share and like thank you
```
### Notes:

* For Kali in Virtualbox, I did have to unplug the adapter once or twice to get the card to show up in IW DEV. Also, within Virtualbox I had to see the USB Controller to USB 2.0 under Settings -> USB. 

* Setup was test using the standard USB, not USB-C. I had to move the USB adapter to different USB slots until the lights were blinking blue.
