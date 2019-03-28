# charmbuntu
Modified 5ilver's Chambian.sh to install Ubuntu 18.04 to ARM Chromebooks
Source: https://github.com/5ilver/charmbian

5silver's description modified here


Ubuntu install script for samsung arm chromebooks. Designed to be run ON the target device from an arch boot stick created from https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2. Copy charmbuntu.sh to partition 2 either when creating the stick, or after you've booted into the usb environment. You will need to use CTRL+U at the dev mode screen, and you cannot boot from the blue usb3 port.

Steps:
- 'bash charmbuntu.sh'
- Select your wifi
- Enter the target device path (/dev/mmcblk0 for internal emmc)
- After installing the packages, it will prompt a password for the new installation
- Wait until it finishes and reboot.

After rebooting:
- Select user "root" and write your password
- 'iwconfig mlan0 essid <your_wifi> key s:<your_wifi_key>
- 'ip link set mlan0 up'
- 'dhclient mlan0'
- install your favorite lightwight desktop environment (lxde or xfce4 recommended)

The magic

The magic part is just a honking debootstrap command to build a usable debian root from upstream sources using the arch kernel and modules to get you off of google's udders. It then does a few useful tweaks to make the system usable on first boot.

But what does it dooooooo?

Partitions your device
Copies arch kernel and modules
Grabs debootstrap
Debootstraps a ubuntu system
Puts a nice trackpad config in place
Disables DPMS in xorg
Sleep hacks in ACPI to disable KB/mouse wake when lid is closed
Sets up a WPA wifi connection with wpa_passphrase(if desired)
