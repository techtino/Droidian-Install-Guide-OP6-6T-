# Droidian Guide


## NOTE: Droidian have a new installer, I suggest following the upstream guide https://devices.droidian.org/#/devices/enchilada for steps after flashing android 9.


# What is Droidian?

Droidian is a Linux distribution for Android Phones based on Mobian, and therefore supports all Debian applications. It runs on a large majority of Android 9 devices. If a device has been ported to Ubuntu Touch and is android 9 or 10, it is likely possible to run Droidian.

Dependencies:
Fastboot and ADB (On Arch these can be found in the android-tools package)

# Downgrading to Android 9

Since the OnePlus 6T currently has a Halium build based on Android 9, we need to make sure our device is running Android 9 before Droidian can be installed.

This can be done by flashing OOS 9 to the phone using TWRP or MSM Download Tool.

If you have Android 9 already installed, skip to "Preparing files for droidian".

### TWRP Method

Firstly, download the OOS 9 zip from:

[For OnePlus 6](https://otafsg1.h2os.com/patch/amazone2/GLO/OnePlus6Oxygen/OnePlus6Oxygen_22.O.34_GLO_034_1909112343/OnePlus6Oxygen_22_OTA_034_all_1909112343_dd26.zip)

[For OnePlus 6T](https://otafsg1.h2os.com/patch/amazone2/GLO/OnePlus6TOxygen/OnePlus6TOxygen_34.O.24_GLO_024_1909112343/OnePlus6TOxygen_34_OTA_024_all_1909112343_d5b1905.zip)

Also, download TWRP 3.5.2 for your respective device. You can use 3.6 instead for android 11.

[For OnePlus 6](https://eu.dl.twrp.me/enchilada/twrp-3.5.2_9-0-enchilada.img.html)

[For OnePlus 6T](https://eu.dl.twrp.me/fajita/twrp-3.5.2_9-0-fajita.img.html)

Once these are saved, you can load your device into fastboot mode. 
On the OnePlus 6 this can be done by holding POWER + VOL UP.
On the OnePlus 6T this can be done by holding VOL UP + VOL DOWN + POWER, hold these until you see fastboot mode appear.

Connect the phone to your machine with a USB cable.

Next, we can boot TWRP 3.5.2:

    sudo fastboot boot twrp-3.5.2_9-0-[device].img
    
   From TWRP, select Advanced, then Sideload.
   Then run the command:

    sudo adb sideload OnePlus6Oxygen_22_OTA_034_all_1909112343_dd26.zip

   (Change the filename depending on which is required for your device)
   
Select reboot from TWRP, then Bootloader.

Once fastboot mode loads once again, we should have OOS 9 installed to our currently booted slot, which means we are ready to install Droidian!

### MSM Download Tool Method

[Follow the steps here](https://forum.xda-developers.com/t/tool-6t-msmdownloadtool-v4-0-59-oos-v9-0-13.3867448/)

# Preparing files required for Droidian

First we need to download a few things. TWRP 3.3.1, the droidian zips and our boot image.
### TWRP
[For OnePlus 6](https://eu.dl.twrp.me/enchilada/twrp-3.3.1-2-enchilada.img.html)

[For OnePlus 6T](https://eu.dl.twrp.me/fajita/twrp-3.3.1-1-fajita.img.html)

### Droidian Zips
[Download the latest stable droidian zips from here](https://github.com/droidian-images/droidian/releases)

Specifically we want the arm64 rootfs and optionally the devtools if we wish to have additional features such as SSHing from a PC.

Optionally, if you are feeling brave, then you can use the latest nightlies [here](https://github.com/droidian-images/droidian/releases/tag/nightly) instead but there are chances for random issues.

### Boot image for OnePlus 6 and 6T
[Get it Here](https://github.com/techtino/Droidian-Install-Guide-OP6-6T-/raw/main/halium-boot.img)
Boot image built by: https://github.com/MrCyjaneK (He's put a bunch of work into the kernel)

# Installing Droidian
Load the phone into fastboot mode, then run:

    sudo fastboot flash boot halium-boot.img
    sudo fastboot boot twrp-3.3.1-2-[device].img
Go to Advanced, then click Sideload and run:

    sudo adb sideload droidian-rootfs-api28gsi-arm64_[date].zip
    sudo adb sideload droidian-devtools-arm64_[date].zip

All Done, press reboot, then system in TWRP and you'll be greeted with Phosh!
BTW, default password is 1234, probably want to change that :D

# Droidian Tips and tricks
[Take a look here](https://pad.mrcyjanek.net/p/r.901550d73e46cfeced7e4f12e969d120)
It'll probably cover most of the things you need :D
