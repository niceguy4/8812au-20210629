### Credit: https://www.youtube.com/watch?v=Yr-8RmoNi70&t and whoever made 8812au-20210629-main

### Device: ALFA AWUS036ACH - https://www.amazon.com/dp/B08SJC78FH

### Chipset: Realtek RTL8812AU 

### Issue: 
  Device no showing up in Kali Linux
  Device showing up but not collecting/catching clients

My setup is Windows 11 running virtual machine using VMWare for Kali (kali-linux-2024.2-vmware-amd64). 

I uninstalled the Windows 11 drivers for Realtek RTL8812AU including the ulitity app. Restarted computer and then plugged USB wireless adapter back into USB slot (make sure blue light blinks or move to another USB slot)
Go to Windows Device Manager, right click on the adapter uner Network Adapters, Update Driver, Search automatically for Drivers
Load Kali Linux using VMWare
And then following intructions from 
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
www.mediafire.com/file/tuyze3vc65zckne/8812au-20210629-main.zip/file

open terminal 
inter this command 
sudo apt-get install bc mokutil build-essential libelf-dev linux-headers-`uname -r`

Next 
sudo ./install-driver.sh
after its done click N then Y then reboot the system 
you are good to go your ALFA awus036ach ac1200 will be working without any issue 

if this fix your issue please share and like thank you
```
