# Заметки и прочее

Прочтите все! Ниже вы найдете инструкцию по установке.
[English Instruction/Английская инструкция](https://github.com/ubports-oneplus6/documentation/blob/master/README.md)
# Присоеденяйтесь к нашему Discord-серверу!

https://discord.gg/haVG9Ga [У нас есть много причин для этого!](https://imgur.com/a/WM9ZNDc).

# Статус прошивки

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

# Статус сборки

|         Компонент | Статус |
|------------------:|:-------|
|   halium-boot.img | [![Статус сборки](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/badge/icon)](https://oldpc.mrcyjanek.net:443/ci/job/ubports-oneplus6-android_kernel_oneplus_sdm845/) |

# Как установить данную ОС?

 * [Стоковая прошивка, TWRP и прочие вещи для fajita (6T)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/fajita)
 * [Стоковая прошивка для enchilada (6)](https://oldpc.mrcyjanek.net/files/all/Documents/Porting/enchilada)

## Загрузки
Скачать Ubuntu Touch можно отюда: https://oldpc.mrcyjanek.net/ci/job/ubports-gsi-make-flashable-zip/
Зеркало для более высокой скорости скачивания: https://build.connolly.tech/ubports/ (target.zip)

Set it going whilst reading the information and instructions below.

## Важная информация

OnePlus 6(T) поддерживает функцию, известную как слоты, предназначенную для обеспечения бесшовных обновлений, не прерывая работу пользователя, кроме перезагрузки. Функционально это означает, что на устройствах есть 2 из всех важных системных разделов, это здорово для нас, так как мы можем использовать это в наших интересах, установив Android на одном и ubuntu touch в другом, что позволяет пользователям выполнять привязанную двойную загрузку - для теперь для переключения ОС требуется ПК.

Это руководство, если следовать ему правильно, сохранит вашу существующую систему Android и все ваши данные, что позволит вам в любое время переключиться обратно. Также предполагается, что вы в настоящее время используете прошивку на базе Android 10.

Вам понадобится скачать последние версии Android SDK, их можно получить здесь.: https://developer.android.com/studio/releases/platform-tools, или для Arch Linux `pacman -S android-tools`

## Инструкция по устновке

1. Откат на OOS 9 - это необходимо, а ubuntu touch не работает с Android 10
    * Загрузите стоковую OOS 9 для своего устройства по ссылкам выше, вам нужно `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`.
    * К сожалению, вам понадобятся 2 разные версии TWRP, если вы хотите использовать двойную загрузку, загрузите последнюю версию для Android 10. - [Enchilada](https://eu.dl.twrp.me/enchilada/twrp-3.4.0-3-enchilada.img.html)/[Fajita](https://dl.twrp.me/fajita/twrp-3.4.0-1-fajita.img.html) для более старой версии Android 9 [Enchilada](https://eu.dl.twrp.me/enchilada/twrp-3.3.1-2-enchilada.img.html)/[Fajita](https://dl.twrp.me/fajita/twrp-3.3.1-1-fajita.img.html).
    * Выключите устройство, а затем включите его, удерживая увеличение и уменьшение громкости, теперь вы должны быть на экране [Как здесь](https://gist.github.com/Jim-Bar/a74dc9f45d049340c2a8576f2bdef701#file-oneplus_6_bootloader-jpg).
    * Теперь загрузитесь в TWRP через FastBoot `fastboot boot twrp-3.4.0-3-<device>.img`, после включения на главном экране вы должны увидеть свой телефон в `adb devices` на вашем ПК.
    * Переместите zip-файл OxygenOS 9 на свое устройство с помощью `adb push OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip /sdcard`
    * В TWRP зайдите в установку и выберите `OnePlus6TOxygen_twrp_34_OTA_android_9_Pie.zip`. Проведите пальцем, чтобы подтвердить установку, и подождите, это займет несколько минут. Обратите внимание, что это установит его в другой слот, это не повлияет на любую систему Android, которую вы сейчас используете.
    * Как только это будет сделано, перейдите в меню перезагрузки и выберите `bootloader`, затем перезагрузитесь. Вы должны быть в загрузчике - на черном экране с надписью `START` зелеными буквами, как и раньше, однако теперь вы находитесь в другом слоте (в который вы только что установили Android 9).
2. Установите Ubuntu Touch
    * Если это еще не в загрузчике, выключите устройство и войдите в него, удерживая 2 кнопки громкость и питание.
    * Загрузитесь в TWRP 3.3 (тот, что для Andorid 9) через `fastboot boot twrp-3.3.1-<device>.img`
    * Скопируйте установщик Ubuntu Touch на устройство через `adb push target.zip /sdcard`
    * Установите его из меню `install` в TWRP.
3. Установите ядро
    * После установки системы, идет ядро. Снова в меню перезагрузки выберите «bootloader».
    * Находясь в загрузчике, запустите `fastboot flash boot halium-boot.img`.
4. Установите ramdisk - этот шаг будет удален в будущем обновлении.
    * Скачайте RamDisk (Отсюда)[https://oldpc.mrcyjanek.net/files/:D/Documents/Porting/fajita/ubuntu-touch/zips/halium-ramdisk-2020.06.20.zip]
    * Загрузитесь обратно в TWRP с помощью `fastboot boot twrp-3.3.1-<device>.img`.
    * `adb push halium-ramdisk-2020.06.20.zip`
    * Зайдите в установку и выберите `halium-ramdisk-2020.06.20.zip`
5. Выберите систему в меню перезагрузки TWRP, не устанавливайте приложение TWRP!
Наслаждайтесь своей новой системой
1734895. Теперь все должно работать! c:

## Возвращение в Android
* Выключите устройство, удерживайте увеличение и уменьшение громкости, и питание, чтобы войти в режим загрузчика.
* Запустите `fastboot getvar current-slot`, это скажет вам, в какой слот установлен ubuntu touch.
* Переключите слоты, если ваш текущий слот `a` тогда запустите `fastboot --set-active=b`, если `b` выполните `--set-active=a`.
* `fastboot reboot`

Те же шаги можно использовать для повторного переключения на Ubuntu Touch.
