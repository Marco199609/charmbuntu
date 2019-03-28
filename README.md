# charmbuntu
Modified 5ilver's Chambian.sh to install Ubuntu 18.04 to ARM Chromebooks
Source: https://github.com/5ilver/charmbian

5silver's description modified here


Ubuntu install script for samsung arm chromebooks. Designed to be run ON the target device from an arch boot stick created from https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2. Copy charmbuntu.sh to partition 2 either when creating the stick, or after you've booted into the usb environment. You will need to use CTRL+u at the dev mode screen, and you cannot boot from the blue usb3 port.

To run, just 'bash charmbuntu.sh', then select your wifi, enter the target device path (/dev/mmcblk0 for internal emmc), and hurry up and wait.

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
