# Setting up a Raspberry PI with Etherner of USB-C for use with iPad Pro

- `Burn a micro SD card with Ubuntu 22.04.1 server 64bit on it`
    - Preconfigure the wlan in the raspberry pi imager (control+shift+x)
    - Preconfigure the username (ex: patrick)
    - Set the hostname to "pi" <br>
    <br>
- `Start rapi with it`
    - From another linux machine or macbook
        - from your home directory create an identity: `ssh-keygen -t rsa -b 4096 -f .ssh/patrick@pi.local`
        - push it to the the raspi: `ssh-copy-id -i ~/.ssh/patrick\@pi.local.pub patrick@pi.local`
        - 
    - Install net-tools: `sudo apt install net-tools`
    - `vi /boot/firmware/config.txt`<br>
       Add the following to the [all] section at the end<br>
       `dtoverlay=dwc2,dr_mode=peripheral`<br>
       save and exit
    - sudo vi /boot/firmware/cmdline.txt
    - modules-load=dwc2,g_ether
    - sudo vi /etc/netplan/99_config.yaml
    - `network:`<br>
      `   version: 2`<br>
      `   renderer: networkd`<br>
      `   ethernets:`<br>
      `     usb0:`<br>
      `     addresses:`<br>
      `       - 10.10.10.2/24`<br>
    - sudo netplan apply
    - sudo apt install dnsmasq
    - `interface=usb0`<br>
      `version: 2`<br>
      `renderer: networkd`<br>
      `ethernets:`<br>
    


