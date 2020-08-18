# Notes and things

Read everything, on the bottom you will find installation instructions.
[Russian Instruction/Русская иструкция](https://github.com/ubports-oneplus6/documentation/blob/master/README.ru.md)
# Join our discord

https://discord.gg/haVG9Ga [There are many reasons for joining it](https://imgur.com/a/WM9ZNDc).

# Port status

|         Component | Status | Details            |
|------------------:|:------:|--------------------|
|          AppArmor |    Y   |                    |
|      Boot into UI |    Y   |                    |
|            Camera |    Y   | If app crashes after taking photo try switching cameras and turning flash on, and off. |
|       Phone Calls |    Y   |  Only works on SIM2, you will have to move your SIM card. |
|     Cellular Data |    Y   |                    |
|               GPS |    Y   |                    |
|           Sensors |    Y   |                    |
|             Sound |    Y   |                    |
| UBPorts Installer |    N   |                    |
|  UBPorts Recovery |    N   |                    |
|          Vibrator |    Y   |                    |
|             Wi-Fi |    Y   | Occasionally disconnects while device is sleeping. |

# Build status

|         Component | Status |
|------------------:|:-------|
|   halium-boot.img | [![Build Status](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/badge/icon)](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/) |

# How to install this OS?

 * [Stock rom, twrp and stuff for fajita (6T)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/fajita)
 * [Stock rom for enchilada (6)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/enchilada)

# Downloads
Download Ubuntu Touch from https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/
or from the mirror: https://build.connolly.tech/ubports/ (target.zip)

Set it going whilst reading the information and instructions below.

## Some preliminary information

The OnePlus 6/T supports a feature known as slots, designed to allow for seamless updates without interrupting the user other than to reboot. Functionally, this means the devices have 2 of all the important system partitions, this is great for us as we can use it to our advantage by installing Android on one and ubuntu touch on the other, allowing users to perform a tethered dual boot - for now switching OS requires a PC.

This guide if followed correctly will preserve your existing Android system and all your data, allowing you to switch back whenever you please. It also assumes you are currently running some Android 10 based ROM.

You will need the lates Android tools, they can be fetched from here: https://developer.android.com/studio/releases/platform-tools, on Arch linux `pacman -S android-tools`

## Installation instructions

1. Downgrade to OOS 9 - this is needed and ubuntu touch doesn't work with Android 10 base
    * Download stock OOS 9 for your device from links above, you need `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`.
    * You will unfortunately need 2 different TWRP versions if your wish to dual boot, download the latest for Android 10 - [Enchilada](https://eu.dl.twrp.me/enchilada/twrp-3.4.0-3-enchilada.img.html)/[Fajita](https://dl.twrp.me/fajita/twrp-3.4.0-1-fajita.img.html) and an older version for Android 9 [Enchilada](https://eu.dl.twrp.me/enchilada/twrp-3.3.1-2-enchilada.img.html)/[Fajita](https://dl.twrp.me/fajita/twrp-3.3.1-1-fajita.img.html).
    * Power off your device and then turn it on while holding volume up, you should now be on a screen [like this](https://gist.github.com/Jim-Bar/a74dc9f45d049340c2a8576f2bdef701#file-oneplus_6_bootloader-jpg).
    * Now boot into TWRP recovery with the command `fastboot boot twrp-3.4.0-3-<device>.img`, once on on the main screen, you should see your phone in `adb devices` on your PC.
    * Move OxygenOS 9 zip file to your device with `adb push OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip /sdcard`
    * In TWRP go to install and choose `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`. Swipe to confirm flash and wait, it will take a few minutes. Note that this will install it to your other slot, it won't affect whatever Android system you're currently running.
    * Once it's done, go to the reboot menu and pick `bootloader`, then hit reboot. You should be in the bootloader - on a black screen with `START` in green letters like before, however you're now on the other slot (the one you just installed Android 9 to).
2. Flash Ubuntu Touch
    * If not already in the bootloader, power off the device and enter it by holding volume up and power.
    * Boot into TWRP 3.3 (the one for Andorid 9) with `fastboot boot twrp-3.3.1-<device>.img`
    * Copy the Ubuntu Touch installer to the device with `adb push target.zip /sdcard`
    * Install it from `install` menu in TWRP.
3. Flash kernel
    * With the system installed, next is the kernel, from the reboot menu pick `bootloader` again.
    * Whilst in the bootloader, run `fastboot flash boot halium-boot.img`.
4. Flash the ramdisk - this step will be removed in a future update.
    * Download https://oldpc.mrcyjanek.net/files/:D/Documents/Porting/fajita/ubuntu-touch/zips/halium-ramdisk-2020.06.20.zip
    * Boot back into TWRP with `fastboot boot twrp-3.3.1-<device>.img`.
    * `adb push halium-ramdisk-2020.06.20.zip`
    * Go to install and pick `halium-ramdisk-2020.06.20.zip`
5. Choose system from TWRP reboot menu, don't install the TWRP app!
Enjoy your new system
1734895. Everything should be working now c:

## Switching back to Android
* Power off the device, hold volume up and power to enter bootloader mode.
* Run `fastboot getvar current-slot`, this will tell you which slot ubuntu touch is installed to.
* Switch slots, if your current slot is `a` then run `fastboot --set-active=b`, if it's `b` use `--set-active=a`.
* `fastboot reboot`

The same steps can be used to switch to Ubuntu Touch again.
