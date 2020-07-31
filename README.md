# Notes and things

Read everything, on the bottom you will find installation instructions.

# Join our discord

https://discord.gg/haVG9Ga [There are many reasons for joining it](https://imgur.com/a/WM9ZNDc).

# Port status

|         Component | Status | Details            |
|------------------:|:------:|--------------------|
|          AppArmor |    Y   |                    |
|      Boot into UI |    Y   | [Screen turns black after few seconds](https://github.com/ubports-oneplus6/documentation/issues/4) |
|            Camera |    Y   | If app crashes after taking photo try switching cameras and turning flash on, and off. |
|    Cellular Calls |    Y   | [Calls not working on 1 sim](https://github.com/ubports-oneplus6/documentation/issues/2) |
|     Cellular Data |    Y   |                    |
|               GPS |    Y   |                    |
|           Sensors |    Y   |                    |
|             Sound |    Y   |                    |
| UBPorts Installer |    N   |                    |
|  UBPorts Recovery |    N   |                    |
|          Vibrator |    Y   |                    |
|             Wi-Fi |    Y   | Sometimes (not often) you get disconnected when screen is off. |

# Build status

|         Component | Status |
|------------------:|:-------|
|   halium-boot.img | [![Build Status](https://oldpc.mrcyjanek.net:443/ci/job/android_kernel_oneplus_sdm845/badge/icon)](https://oldpc.mrcyjanek.net:443/ci/job/android_kernel_oneplus_sdm845/) |
|       ubports-gsi | [ask them](https://github.com/ubports-gsi/projectmanagement) or [download target.zip](https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/)   |

# How to install

 * [Stock rom, twrp and stuff for fajita (6T)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/fajita)
 * [Stock rom for enchilada (6)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/enchilada)

1. Flash stock 9
    * _You should have file named `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip` in your working directory._
    * Boot to twrp by using `fastboot boot twrp-pie.img` # Assuming that you have it in your current directory
    * Move .zip file to sdcard by using `adb push OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip /sdcard`
    * In twrp go to install and flash `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`.
    * go to reboot and change slot then repeat point 1.3
2. Format data
    * _Optional step: check if stock 9 works by doing reboot -> system_
    * Boot to twrp go to wipe and click `Format data`, if asked type 'yes'.
3. Flash gsi
    * _Download GSI from https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/_
    * Boot to twrp
    * move `target.zip` file to `/sdcard` by using
        ```adb push target.zip /sdcard```
    * Install it from `install` menu in twrp
4. Flash kernel
    * boot to fastboot
    * type `fastboot flash boot halium-boot.img`
5. Flash `halium-ramdisk`
    * _Download it from here https://oldpc.mrcyjanek.net/files/:D/Documents/Porting/fajita/ubuntu-touch/zips/halium-ramdisk-2020.06.20.zip_
    * Boot to twrp
    * Move `halium-ramdisk*.zip` by using
        ```adb push halium-ramdisk*.zip /sdcard```
    * Go to install and install zip
6. Reboot
1734895. Everything should be working now c:


