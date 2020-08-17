# Notes and things

Прочтите все! Нижу вы найдете инструкцию по установке.

# Присоеденяйтесь к нашему Discord-серверу

https://discord.gg/haVG9Ga [У нас есть множество причин для этого!](https://imgur.com/a/WM9ZNDc).

# Статус порта

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

# Статус сборки

|         Component | Status |
|------------------:|:-------|
|   halium-boot.img | [![Build Status](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/badge/icon)](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/) |
|       ubports-gsi | [Узнайте тут](https://github.com/ubports-gsi/projectmanagement) or [Скачать target.zip](https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/)   |

# Как установить данную OS?

 * [Стоковая прошивка, TWRP и прочие файлы для OnePlus Fajita (6T)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/fajita)
 * [Стоковая прошивка для OnePlus Enchilada (6)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/enchilada)

1. Установите OxygenOS 9
    * _У вас должен быть файл с именем `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip` в вашем рабочем каталоге._
    * Загрузитесь в TWRP используя команду `fastboot boot twrp-pie.img` # Предполагая, что он у вас есть в вашем текущем каталоге
    * Поместите .zip файл во внутреннюю память используя `adb push OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip /sdcard`
    * В TWRP перейдите в пункт Установка и прошейте .zip файл `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`.
    * перезагрузитесь и повторите данные действия заново! # Это требуется для устновки в 2 слота! 1.3
2. Отформатируйте раздел DATA
    * _Необязательный шаг: проверьте работает ли стоковая система Перезагрузка -> Система_
    * Загрузитесь в TWRP, перейдите в меню Очистка и кликните `Форматировать Data`, и пропишите 'yes'.
3. Прошейте GSI
    * _Скачайте GSI с сайта https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/_ или https://build.connolly.tech/ubports/ (target.zip)
    * Загрузитесь в TWRP
    * Поместиите `target.zip` в `/sdcard` используя
        ```adb push target.zip /sdcard``` или ```MTP```
    * Перейдите в меню `Установка` в TWRP и прошейте этот файл.
4. Установите ядро Halium
    * Перезагрузитесь в FastBoot
    * Пропишите `fastboot flash boot halium-boot.img`
5. Установите `halium-ramdisk`
    * _Скачайте его с https://oldpc.mrcyjanek.net/files/:D/Documents/Porting/fajita/ubuntu-touch/zips/halium-ramdisk-2020.06.20.zip_
    * Загрузитесь в TWRP
    * поместите `halium-ramdisk*.zip` используя
        ```adb push halium-ramdisk*.zip /sdcard``` или ```MTP```
    * Перейдите в меню `Установка` в TWRP и прошейте этот файл.
6. Перезагрузитесь в систему!
1734895. Теперь все должно работать c:


